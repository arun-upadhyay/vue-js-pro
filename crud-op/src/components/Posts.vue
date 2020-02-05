<template>
    <div>
        <h1>Posts</h1>
        <span>Total Post <b>{{totalPost}}</b></span>
        <div v-bind:key="post._id" v-for="post in posts">
            <Post v-bind:post="post"></Post>
        </div>
    </div>
</template>

<script>
    import Post from "./Post";

    export default {
        name: "Posts",
        props: ["posts"],
        components: {
            Post
        },
        computed: {
            totalPost: function () {
                return this.posts.length;
            }
        }
    }
</script>

<style scoped>

</style>
