<template>
    <div>
        <h1>{{post.title}}</h1>
        <p>{{post.description}}</p>

    </div>
</template>

<script>
    export default {
        name: "Post",
        props: ["post"],
    }
</script>

<style scoped>

</style>
