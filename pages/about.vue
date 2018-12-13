<template>
  <div>
    <section class="hero is-small is-primary is-bold">
      <div class="hero-body">
        <div class="container">
          <h1 class="title">
            Blog
          </h1>
          <h2 class="subtitle">
            つらつらと
          </h2>
        </div>
      </div>
    </section>
    <div v-for="post in posts" :key="post.id">
      <section class="section blog-content">
        <div class="container">
          <h1 class="title has-text-weight-bold">{{ post.title }}</h1>
          <h2 class="subtitle">{{ formatDate(post.createdAt) }}</h2>
          <div class="content" v-html="convertHTML(post.content)"></div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import posts from '~/apollo/queries/posts'
import MarkdownIt from 'markdown-it'
import format from 'date-fns/format'
import ja from 'date-fns/locale/ja'

export default {
  head: {
    title: 'Blog'
  },
  name: 'posts',
  data () {
    return {
      posts: {}
    }
  },
  methods: {
    convertHTML: function (markdownText) {
      const md = MarkdownIt()
      return md.render(markdownText)
    },
    formatDate: function (date) {
      const result = format(
        date,
        'YYYY/MM/DD HH:mm:ss',
        {locale: ja}
      )

      return result
    }
  },
  apollo: {
    posts: {
      prefetch: true,
      query: posts
    }
  }
}
</script>

<style>
.blog-content .title {
  font-weight: 600;
}

.blog-content .subtitle {
  font-weight: 600;
}
</style>

