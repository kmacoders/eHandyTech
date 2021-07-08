<template>
  <section>
    <div class="container">
      <h1 class="title is-3 mt-3 mb-3 is-flex is-justify-content-center is-align-items-center">
        All Tags
      </h1>
      <ul class="columns">
        <li v-for="tag in tags" :key="tag" class="column">
          <nuxt-link
            :to="{ name: 'tags-tag', params: { tag: tag.toLowerCase() } }"
            class="text-4xl hover:underline"
          >
            {{ tag }}
          </nuxt-link>
        </li>
      </ul>
    </div>
  </section>
</template>

<script lang="ts">
import { IContentDocument } from '@nuxt/content/types/content'
import { Vue, Component } from 'nuxt-property-decorator'

@Component({
  name: 'TagListPage',
  async asyncData ({ $content }) {
    function onlyUnique (value: string, index: number, self: string[]) {
      return self.indexOf(value) === index
    }

    const blog: IContentDocument[] = await $content('blog', { deep: true })
      .only(['tags'])
      .fetch<IContentDocument[]>()

    /**
     * Tags của tất cả pài viết
     */
    const tags = blog
      .flatMap(blog => blog.tags)
      .filter(onlyUnique)

    return {
      tags
    }
  },
  head () {
    return {
      title: 'Article Tags - Learning Laravel and VueJS',
      link: [
        {
          hid: 'canonical',
          rel: 'canonical',
          href: `${process.env.baseUrl}/tags`
        }
      ]
    }
  }
})
export default class TagListPage extends Vue {}
</script>
