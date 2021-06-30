<template>
  <div class="columns featured-post is-multiline">
    <div class="column is-12 post">
      <article class="columns featured">
        <div class="column is-7 post-img ">
          <img :src="firstBlog.image" :alt="firstBlog.title">
        </div>
        <div class="column is-5 featured-content va">
          <div>
            <h3 class="heading post-category">
              <NuxtLink
                v-for="(tag, index) in firstBlog.tags"
                :key="index"
                to="/"
              >
                {{ tag }}
              </NuxtLink>
            </h3>
            <h1 class="title post-title">
              {{ firstBlog.title }}
            </h1>
            <p class="post-excerpt">
              {{ firstBlog.description }}
            </p>
            <br>
            <NuxtLink :to="firstBlog.path" class="button is-primary">
              Read More
            </NuxtLink>
          </div>
        </div>
      </article>
    </div>
  </div>
</template>

<script>
import { Vue, Component } from 'nuxt-property-decorator'

@Component({
  props: {
    firstBlog: {
      type: Object,
      required: true
    }
  }
})
export default class FeaturedBlog extends Vue {
  mounted () {
    console.log(this.firstBlog)
  }
}
</script>
