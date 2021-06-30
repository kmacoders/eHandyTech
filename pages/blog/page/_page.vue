<template>
  <section class="blog-posts">
    <div class="container">
      <div class="columns">
        <div class="column is-10 is-offset-1">
          <FeaturedBlog />
          <hr>
          <ListBlog />
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { Vue, Component } from 'nuxt-property-decorator'
import FeaturedBlog from '@/components/organisms/FeaturedBlog'
import ListBlog from '@/components/organisms/ListBlog.vue'

@Component({
  components: {
    FeaturedBlog,
    ListBlog
  }
})
export default class PageBlog extends Vue {
}
</script>
<style>
.va {
  display: flex;
  align-items: center;
}

.blog-posts {
  min-height: 100vh;
  padding-top: 4rem;
  padding-bottom: 10rem;
}

.blog-posts article {
  padding: 1.5rem;
}

.blog-posts .post img {
  border-radius: 6px;
}

.blog-posts .post .post-category {
  color: #3b7adf;
}

.blog-posts .post .post-title {
  font-size: 2.2rem;
}

.blog-posts .post .post-excerpt {
  line-height: 1.5rem;
  letter-spacing: 0.03rem;
  font-size: 1.2rem;
  font-family: 'IBM Plex Serif', serif;
}

.blog-posts .post .featured .featured-image img {
  height: 380px;
}
</style>
