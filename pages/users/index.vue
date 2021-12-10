<template>
    <div>
        <ul>
            <li v-for="customer in customers" :key="customer.id">
                {{ customer.name }}
            </li>
        </ul>
        <pagination v-if="pagination.last_page > 1"
                            :pagination="pagination"
                            :offset="5"
                            @paginate="getData()"
                            ></pagination>
    </div>
</template>
<script>
import axios from 'axios'
    export default {
        data() {
            return {
                customers: [],
                pagination: {
                        current_page:1,
                }
            }
        },
        mounted() {
            console.log('Component mounted.')
            this.getData();
        },
        methods: {
            getData() {
                axios.get('http://localhost/laravel/mini-blog/api/users?page='+this.pagination.current_page)
                .then(response => {
                    this.customers = response.data.data;
                    this.pagination = response.data.meta;
                    console.log(response)
                })
                .catch(e => {
                    console.log(e);
                })
            }
        },
    }
</script>