<template>
  <article>
    <h1>{{ mountain.title }}</h1>
    <section>
      <!-- <p></p> -->
      <div v-html="mountain.body"></div>
    </section>
    <button @click="goBack">Back</button>
  </article>
</template>
<script>
export default {
  async asyncData({ $axios, params }) {
    const mountain = await $axios.$get(
      `http://localhost/laravel/mini-blog/api/posts/${params.slug}`
    )
    return { mountain }
  },
  methods: {
    goBack() {
      return this.$router.go(-1)
    }
  }
}
</script>
<style scoped>
article {
  max-width: 800px;
  margin: 0 auto;
}
img {
  height: 200px;
}
p {
  text-align: left;
}
</style>
