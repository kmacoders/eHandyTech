<template>
  <section class="blog-posts">
    <div class="container">
      <div class="columns">
        <div class="column is-10 is-offset-1">
          <FeaturedBlog :first-blog="allArticles[0]" />
          <hr>
          <ListBlog :list-blogs="paginatedArticles" />
        </div>
      </div>
      <div class="columns">
        <div class="column is-10 is-offset-1">
          <Pagination
            :total="allArticles.length"
            :per-page="perPage"
          />
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { Vue, Component } from 'nuxt-property-decorator'
import getContent from '@/utils/getContent'
import FeaturedBlog from '@/components/organisms/FeaturedBlog'
import ListBlog from '@/components/organisms/ListBlog.vue'

@Component({
  components: {
    FeaturedBlog,
    ListBlog
  },
  async asyncData ({ $content, params, error }) {
    const perPage = 8
    const content = await getContent($content, params, error, 'blog')

    return {
      allArticles: content.allArticles,
      paginatedArticles: content.paginatedArticles,
      perPage
    }
  },
  head () {
    return {
      title: `Blog page ${this.$route.params.page} - eHanndy`,
      link: [
        {
          hid: 'canonical',
          rel: 'canonical',
          href: `${this.$config.baseUrl}/blog/page/${this.$route.params.page}`
        }
      ]
    }
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

.blog-posts nav {
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
