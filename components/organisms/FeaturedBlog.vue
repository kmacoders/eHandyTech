<template>
  <div class="columns featured-post is-multiline">
    <div class="column is-12 post">
      <article class="columns featured">
        <div class="column is-7 post-img ">
          <img src="https://cdn.emk.dev/templates/featured-image.png" alt="">
        </div>
        <div class="column is-5 featured-content va">
          <div>
            <h3 class="heading post-category">
              Category Name
            </h3>
            <h1 class="title post-title">
              Blog Posts Template
            </h1>
            <p class="post-excerpt">
              This template is based off of the official default blog template created by the fine folks over at <a href="https://ghost.io">Ghost</a>. If you are looking for a fully featured blog platform, I highly recommend checking them out!
            </p>
            <br>
            <a href="#" class="button is-primary">Read More</a>
          </div>
        </div>
      </article>
    </div>
  </div>
</template>

<script>
import { Vue, Component } from 'nuxt-property-decorator'

@Component
export default class FeaturedBlog extends Vue {
}
</script>
