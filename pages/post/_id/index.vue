<template>
  <div class="main-content">
    <div class="container">
      <h2 class="title is-2">{{ post.title }}</h2>
      <div v-html="post.content"></div>
      <br>
      <h4 class="title is-5 is-marginless">by <strong>{{ post.createdAt }}</strong> at <strong>{{ post.createdAt }}</strong></h4>
    </div>
  </div>
</template>

<script>
  import post from '~/apollo/queries/post'

  export default {
    // validate ({ params }) {
    //   return /^\d+$/.test(params.id)
    // },
    name: 'post',
    // asyncData ({ params }, callback) {
    //   let post = posts.find(post => post.id === parseInt(params.id))
    //   if (post) {
    //     callback(null, { post })
    //   } else {
    //     callback({ statusCode: 404, message: 'Post not found' })
    //   }
    // },
    data () {
      return {
        post: {}
      }
    },
    apollo: {
      post: {
        query: post,
        variables() {
          return {
            id: this.$route.params.id
          }
        }
      }
    }
  }
</script>