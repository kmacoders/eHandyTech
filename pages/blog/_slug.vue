<template>
  <article class="container content">
    <nuxt-content :document="blogDetail" />
  </article>
</template>

<script>
import { Vue, Component } from 'nuxt-property-decorator'
import global from '@/utils/global'
import getSiteMeta from '@/utils/getSiteMeta'

@Component({
  name: 'ArticlePage',
  async asyncData ({ $content, params }) {
    const findedBlog = await $content('blog', { deep: true })
      .where({ slug: params.slug })
      .fetch()
    const [blogDetail] = findedBlog

    const [prev, next] = await $content('blog', { deep: true })
      .only(['title', 'slug', 'published'])
      .sortBy('published', 'desc')
      .surround(params.slug)
      .fetch()

    const allBlogs = await $content('blog', { deep: true })
      .only(['title', 'description', 'image', 'slug', 'published', 'tags'])
      .sortBy('published', 'desc')
      .fetch()

    const blogsByTag = allBlogs.filter((blog) => {
      const blogTags = blog.tags.map(x => x.toLowerCase())
      return blogTags.includes(blog.tags[0].toLowerCase())
    })

    return {
      blogDetail,
      blogsByTag,
      prev,
      next
    }
  },
  head () {
    return {
      title: this.blogDetail.title,
      meta: [
        ...this.meta,
        {
          property: 'blog:published_time',
          content: this.blogDetail.createdAt
        },
        {
          property: 'blog:modified_time',
          content: this.blogDetail.updatedAt
        },
        {
          property: 'blog:tag',
          content: this.blogDetail.tags ? this.blogDetail.tags.toString() : ''
        },
        { name: 'twitter:label1', content: 'Written by' },
        { name: 'twitter:data1', content: global.author || '' },
        { name: 'twitter:label2', content: 'Filed under' },
        {
          name: 'twitter:data2',
          content: this.blogDetail.tags ? this.blogDetail.tags.toString() : ''
        }
      ],
      link: [
        {
          hid: 'canonical',
          rel: 'canonical',
          href: `${this.$config.baseUrl}/blog/${this.$route.params.slug}`
        }
      ]
    }
  },
  computed: {
    meta () {
      const metaData = {
        type: 'blog',
        title: this.blogDetail.title,
        description: this.blogDetail.description,
        url: `${this.$config.baseUrl}/blog/${this.$route.params.slug}`,
        mainImage: this.blogDetail.image
      }
      return getSiteMeta(metaData)
    }
  }
})
export default class BlogDetail extends Vue {}
</script>
