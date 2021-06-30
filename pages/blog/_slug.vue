<template>
  <article class="container content">
    <nuxt-content :document="article" />
  </article>
</template>

<script>
import { Vue, Component } from 'nuxt-property-decorator'
import global from '@/utils/global'
import getSiteMeta from '@/utils/getSiteMeta'

@Component({
  name: 'ArticlePage',
  async asyncData ({ $content, params }) {
    const article = await $content('blog', params.slug).fetch()

    const [prev, next] = await $content('blog')
      .only(['title', 'slug', 'published'])
      .sortBy('published', 'desc')
      .surround(params.slug)
      .fetch()

    const allBlogs = await $content('blog')
      .only(['title', 'description', 'image', 'slug', 'published', 'tags'])
      .sortBy('published', 'desc')
      .fetch()

    const articlesByTag = allBlogs.filter((article) => {
      const articleTags = article.tags.map(x => x.toLowerCase())
      return articleTags.includes(article.tags[0].toLowerCase())
    })

    return {
      article,
      articlesByTag,
      prev,
      next
    }
  },
  head () {
    return {
      title: this.article.title,
      meta: [
        ...this.meta,
        {
          property: 'article:published_time',
          content: this.article.createdAt
        },
        {
          property: 'article:modified_time',
          content: this.article.updatedAt
        },
        {
          property: 'article:tag',
          content: this.article.tags ? this.article.tags.toString() : ''
        },
        { name: 'twitter:label1', content: 'Written by' },
        { name: 'twitter:data1', content: global.author || '' },
        { name: 'twitter:label2', content: 'Filed under' },
        {
          name: 'twitter:data2',
          content: this.article.tags ? this.article.tags.toString() : ''
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
        type: 'article',
        title: this.article.title,
        description: this.article.description,
        url: `${this.$config.baseUrl}/blog/${this.$route.params.slug}`,
        mainImage: this.article.image
      }
      return getSiteMeta(metaData)
    }
  }
})
export default class BlogDetail extends Vue {}
</script>
