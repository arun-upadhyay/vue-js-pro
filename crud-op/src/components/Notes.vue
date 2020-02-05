<template>
    <div>
        <h1>Notes</h1>
        <div v-bind:key="note._id" v-for="note in notes">
            <Note v-bind:note="note"></Note>
        </div>
    </div>
</template>

<script>
    import Note from "./Note";

    export default {
        name: "Notes",
        props: ["notes"],
        components: {
            Note
        }
    }
</script>

<style scoped>

</style>
