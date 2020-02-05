<template>
    <div id="app">
        <h2>Welcome</h2>
        <Posts v-bind:posts="posts"></Posts>

    </div>
</template>

<script>
    import Posts from './components/Posts'
    import axios from 'axios'

    export default {
        name: "app",
        components: {
            Posts
        },
        data() {
            return {
                posts: this.posts
            }
        },
        created: function () {
            this.fetchPosts();
        },
        methods: {
            fetchPosts: function () {
                var url = 'https://arun-express-api.herokuapp.com/posts';
                axios.get(url)
                    .then(res => {
                        this.posts = res.data
                    });
            }
        }
    }

</script>
<style>
    [v-cloak] {
        display: none;
    }
</style>
