<template lang="">
    <div class="mb-2">
        <nav class="navbar navbar-expand-md navbar-light bg-light">
            <nuxt-link class="navbar-brand" :to="{name: 'index'}">Company Logo</nuxt-link>
            <button class="navbar-toggler d-lg-none" type="button" data-toggle="collapse" data-target="#collapsibleNavId" aria-controls="collapsibleNavId"
                aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="collapsibleNavId">
                <ul class="navbar-nav mr-auto mt-2 mt-lg-0">
                    <li class="nav-item">
                        <nuxt-link class="nav-link" :to="{name: 'posts'}">Posts</nuxt-link>
                    </li>
                    <li class="nav-item">
                        <nuxt-link class="nav-link" :to="{name: 'users'}">Users</nuxt-link>
                    </li>
                    <li class="nav-item">
                        <nuxt-link class="nav-link" :to="{name: 'index'}">Mountains</nuxt-link>
                    </li>
                </ul>
            </div>
        </nav>
    </div>
</template>
<script>
export default {
    
}
</script>
<style lang="">
    
</style>