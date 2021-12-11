<template>
<div class="container-fluid">
    <div class="row">
        <div class="col-md-8">
            <div class="card">
                <div class="card-header">
                    Category By Post list
                </div>
                <div class="card-body">
                    <div v-for="post in categorybyposts.posts" :key="post.id" class="p-4 mb-2" style="border: 1px solid #ddd;">
                        <h4>
                            <NuxtLink :to="{ name: 'posts-slug', params: { slug: post.slug } }">
                                {{ post.title }}
                            </NuxtLink>
                        </h4>
                        <p>{{ post.excerpt }}</p>
                    </div>
                </div>
                <div class="card-footer text-muted">
                    pagination will be here
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
                <li v-for="category in categories" :key="category.id">
                  <NuxtLink :to="{ name: 'posts-categories-slug', params: { slug: category.slug } }">
                   {{ category.name }}
                  </NuxtLink>
                </li>
              </ul>
            </div>
          </div>
      </div>
    </div>
</div>
</template>
<script>
export default {
  async asyncData({ $axios, params }) {
    const categorybyposts = await $axios.$get(`http://localhost/laravel/mini-blog/api/category/${params.slug}`)
    const categories = await $axios.$get(`http://localhost/laravel/mini-blog/api/category`)
    return { categorybyposts, categories }
  },
  methods: {
    goBack() {
      return this.$router.go(-1)
    }
  }
}
</script>