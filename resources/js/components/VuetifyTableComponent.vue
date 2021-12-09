<template>

    <div class="container">

        <div class="row justify-content-center">

            <div class="col-md-12">

                <nav class="navbar navbar-toggleable-md navbar-light bg-faded">

                    <a href="/admin/blog/posts/create" class="btn btn-primary">Додати</a>

                </nav>

                <div class="card">

                    <div class="card-body">



                        <v-data-table

                            :headers="headers"

                            :items="posts"

                            :items-per-page="5"

                            class="elevation-1"

                        ></v-data-table>



                    </div>

                </div>

            </div>

        </div>

    </div>

</template>



<script>

export default {

    data() {

        return {

            headers: [

                {

                    text: '#id',

                    align: 'start',

                    sortable: false,

                    value: 'id',

                },

                { text: 'Автор', value: 'user.name' },

                { text: 'Категорія', value: 'category.title' },

                { text: 'Заголовок', value: 'title' },

                { text: 'Дата публікації', value: 'published_at' },

            ],

            posts: [],

        }

    },

    methods: {

        getPosts() {

            axios.get('/api/blog/posts')

                .then(response => {

                    console.log(response);

                    this.posts = response.data;

                });

        },

    },

    mounted() {

        this.getPosts();

    }

}

</script>
