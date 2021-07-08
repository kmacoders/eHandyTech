<template>
  <section>
    <h1>All tag</h1>
    <ul>
      <li v-for="tag in tags" :key="tag" class="text-center mb-2">
        <nuxt-link
          :to="{ name: 'tags-tag', params: { tag: tag.toLowerCase() } }"
          class="text-4xl hover:underline"
        >
          {{ tag }}
        </nuxt-link>
      </li>
    </ul>
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
