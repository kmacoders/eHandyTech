<template>
  <div>
    <div class="flex justify-center">
      <h2
        class="text-center text-3xl mb-4 uppercase bg-black text-white inline-block mx-auto px-2"
      >
        All Tags
      </h2>
    </div>
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
  </div>
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
    const blog: IContentDocument[] = await $content('blog')
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
