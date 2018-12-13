<template>
  <section class="main-content">
    <div class="container">
      <h1 class="title">
        Blog
      </h1>
      <div class="columns is-multiline">
        <div class="column is-half" v-for="post in posts" :key="post.id">
          <div class="card">
            <header class="card-header">
            <p class="card-header-title">
              {{ post.title }}
            </p>
          </header>
          <div class="card-content">
            <div class="content">
              {{ post.title }}
              <br>
              <small>
                by <strong>{{ post.title }}</strong> 
                \\ {{ post.createdAt }}
              </small>
            </div>
          </div>
          <footer class="card-footer">
            <nuxt-link :to="`/post/${post.id}`" 
              class="card-footer-item">
              Read More
            </nuxt-link>
          </footer>
        </div>
      </div>
    </div>
  </div>
</section>
</template>

<script>
  import posts from '~/apollo/queries/posts'

  export default {
    name: 'posts',
    data () {
      return {
        posts: {}
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