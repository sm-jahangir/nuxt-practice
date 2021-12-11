<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col col-md-8">
        <div class="card">
          <div class="card-header">
            <h3>Post List</h3>
          </div>
          <div class="card-body">
            <div v-for="post in posts" :key="post.id">
              <div style="border: 1px solid #ddd;padding:5px;">
                <h4 class="card-title ml-4">
                  <NuxtLink :to="{ name: 'posts-slug', params: { slug: post.slug } }">
                    {{ post.title }}
                  </NuxtLink>
                </h4>
                <p class="card-text ml-4">  {{ post.excerpt }}</p>
              </div>
              <br><br>
            </div>
          </div>
          <div class="card-footer text-muted">
            Pagination will be Here
          </div>
        </div>
      </div>
      <div class="col col-md-4">
          <div class="card">
            <div class="card-header">
              Right Sidebar Here
            </div>
            <div class="card-body">
              <ul>
                <li>
                  <a href="">List 1</a>
                </li>
                <li>
                  <a href="">List 1</a>
                </li>
                <li>
                  <a href="">List 1</a>
                </li>
                <li>
                  <a href="">List 1</a>
                </li>
              </ul>
            </div>
          </div>
      </div>
    </div>
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
