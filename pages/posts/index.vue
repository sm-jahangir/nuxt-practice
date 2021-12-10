<template>
  <div class="text-center">
    <h1>Data fetched using asyncData</h1>
    <ul>
      <li v-for="post in posts" :key="post.id">
        <NuxtLink :to="{ name: 'posts-slug', params: { slug: post.slug } }">
          {{ post.title }}
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>
<script>
import axios from 'axios'
export default {
    async asyncData({ $axios }) {
    const posts = await $axios.$get(`http://localhost/laravel/mini-blog/api/posts`)
    return { posts }
  }
}
</script>
