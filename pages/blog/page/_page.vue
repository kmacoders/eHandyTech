<template>
  <section class="blog-posts">
    <div class="container">
      <div class="columns">
        <div class="column is-10 is-offset-1">
          <div class="columns featured-post is-multiline">
            <div class="column is-12 post">
              <FeaturedBlog />
            </div>
          </div>
          <hr>
          <div class="columns is-multiline">
            <div class="column post is-6">
              <article class="columns is-multiline">
                <div class="column is-12 post-img">
                  <img src="https://cdn.emk.dev/templates/post-img.png" alt="Featured Image">
                </div>
                <div class="column is-12 featured-content ">
                  <h3 class="heading post-category">Category Name</h3>
                  <h1 class="title post-title">Slightly Longer Blog Post Title</h1>
                  <p class="post-excerpt">Lorem ipsum dolor sit, amet consectetur adipisicing elit. Accusamus ratione harum eaque, animi nulla tempore quis, quam voluptatum.</p>
                  <br>
                  <a href="#" class="button is-primary">Read More</a>
                </div>
              </article>
            </div>
            <div class="column post is-6">
              <article class="columns is-multiline">
                <div class="column is-12 post-img">
                  <img src="https://cdn.emk.dev/templates/post-img.png" alt="Featured Image">
                </div>
                <div class="column is-12 featured-content ">
                  <h3 class="heading post-category">Category Name</h3>
                  <h1 class="title post-title">Slightly Longer Blog Post Title</h1>
                  <p class="post-excerpt">Lorem ipsum dolor sit, amet consectetur adipisicing elit. Accusamus ratione harum eaque, animi nulla tempore quis, quam voluptatum.</p>
                  <br>
                  <a href="#" class="button is-primary">Read More</a>
                </div>
              </article>
            </div>
            <div class="column post is-4">
              <article class="columns is-multiline">
                <div class="column is-12 post-img">
                  <img src="https://cdn.emk.dev/templates/post-img.png" alt="Featured Image">
                </div>
                <div class="column is-12 featured-content ">
                  <h3 class="heading post-category">Category Name</h3>
                  <h1 class="title post-title">Slightly Longer Blog Post Title</h1>
                  <p class="post-excerpt">Lorem ipsum dolor sit, amet consectetur adipisicing elit. Accusamus ratione harum eaque, animi nulla tempore quis, quam voluptatum.</p>
                  <br>
                  <a href="#" class="button is-primary">Read More</a>
                </div>
              </article>
            </div>
            <div class="column post is-4">
              <article class="columns is-multiline">
                <div class="column is-12 post-img">
                  <img src="https://cdn.emk.dev/templates/post-img.png" alt="Featured Image">
                </div>
                <div class="column is-12 featured-content ">
                  <h3 class="heading post-category">Category Name</h3>
                  <h1 class="title post-title">Slightly Longer Blog Post Title</h1>
                  <p class="post-excerpt">Lorem ipsum dolor sit, amet consectetur adipisicing elit. Accusamus ratione harum eaque, animi nulla tempore quis, quam voluptatum.</p>
                  <br>
                  <a href="#" class="button is-primary">Read More</a>
                </div>
              </article>
            </div>
            <div class="column post is-4">
              <article class="columns is-multiline">
                <div class="column is-12 post-img">
                  <img src="https://cdn.emk.dev/templates/post-img.png" alt="Featured Image">
                </div>
                <div class="column is-12 featured-content ">
                  <h3 class="heading post-category">Category Name</h3>
                  <h1 class="title post-title">Slightly Longer Blog Post Title</h1>
                  <p class="post-excerpt">Lorem ipsum dolor sit, amet consectetur adipisicing elit. Accusamus ratione harum eaque, animi nulla tempore quis, quam voluptatum.</p>
                  <br>
                  <a href="#" class="button is-primary">Read More</a>
                </div>
              </article>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { Vue, Component } from 'nuxt-property-decorator'
import FeaturedBlog from '@/components/organisms/FeaturedBlog'

@Component({
  components: {
    FeaturedBlog
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
