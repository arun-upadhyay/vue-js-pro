<template>
    <div>
        <h1>{{note._id}}</h1>
        <p>{{note.title}}</p>
        <p>{{note.desc}}</p>
    </div>
</template>

<script>
    export default {
        name: "Note",
        props: ["note"]
    }
</script>

<style scoped>

</style>
