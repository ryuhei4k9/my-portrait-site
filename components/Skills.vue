<template>
  <section class="main-content">
    <div class="container">
      <h1 class="title">
        Skills
      </h1>
      <div class="content">
        <dl v-for="skill in skills" :key="skill.id">
          <dt class="has-text-weight-bold">{{ skill.name }}</dt>
          <dd>{{ skill.description }}</dd>
        </dl>
      </div>
    </div>
  </section>
</template>

<script>
  import skills from '~/skills.json'
  export default {
    name: 'skills',
    data () {
      return { skills }
    }
  }
</script>