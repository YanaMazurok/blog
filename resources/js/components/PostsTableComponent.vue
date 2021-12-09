<template>

    <div class="container">

        <div class="row justify-content-center">

            <div class="col-md-12">

                <nav class="navbar navbar-toggleable-md navbar-light bg-faded">

                    <a href="/admin/blog/posts/create" class="btn btn-primary">Додати</a>

                </nav>

                <div class="card">

                    <div class="card-body">

                        <table class="table table-hover">

                            <thead>

                            <tr>

                                <th>#</th>

                                <th>Автор</th>

                                <th>Категорія</th>

                                <th>Заголовок</th>

                                <th>Дата публікації</th>

                            </tr>

                            </thead>

                            <tbody>

                            <tr v-for="post in posts">

                                <td>{{ post.id }}</td>

                                <td>{{ post.user.name }}</td>

                                <td>{{ post.category.title }}</td>

                                <td><a :href="'/admin/blog/posts/' + post.id + '/edit'">{{ post.title }}</a></td>

                                <td>{{ post.published_at }}

                                </td>

                            </tr>

                            </tbody>

                        </table>

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

        console.log('Component mounted.')

        this.getPosts();

    }

}

</script>
