<template>
  <div class="main-content">
    <div class="container">
      <h2 class="title is-2">{{ post.title }}</h2>
      <div class="content" v-html="convertedContent"></div>
      <br>
      <h4 class="title is-5 is-marginless">at <strong>{{ formattedCreatedAt }}</strong></h4>
    </div>
  </div>
</template>

<script>
  import post from '~/apollo/queries/post'
  import MarkdownIt from 'markdown-it'
  import format from 'date-fns/format'
  import ja from 'date-fns/locale/ja'

  export default {
    // validate ({ params }) {
    //   return /^\d+$/.test(params.id)
    // },
    name: 'post',
    data () {
      return {
        post: {}
      }
    },
    computed: {
      convertedContent: function () {
        const md = new MarkdownIt()
        if (this.post.content) {
          return md.render(this.post.content)
        }
      },
      formattedCreatedAt: function () {
        const result = format(
          this.post.createdAt,
          'YYYY/MM/DD HH:mm:ss',
          {locale: ja}
        )

        return result
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