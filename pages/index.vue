<template>
  <div>
    <section class="hero is-medium is-primary is-bold">
      <div class="hero-body">
        <div class="container">
          <h1 class="title">
            Ryuhei Shikanai's Portfolio
          </h1>
          <h2 class="subtitle">
            Web & Application  Engineer
          </h2>
        </div>
      </div>
    </section>
    <about-me/>
    <skills/>
  </div>
</template>

<script>
  import AboutMe from '~/components/AboutMe.vue'
  import Skills from '~/components/Skills.vue'

  export default {
    components: {
      AboutMe,
      Skills
    },
    head: {
      title: 'Home'
    }
  }
</script>
