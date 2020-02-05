<template>
    <div>
        <h1>{{note.title}}</h1>
        <p>{{note.description}}</p>
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
