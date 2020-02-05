<template>
    <div id="app">
        <h2>Welcome</h2>
        <Notes v-bind:notes="notes"></Notes>

    </div>
</template>

<script>

    import Notes from './components/Notes'

    export default {
        name: "app",
        components: {
            Notes
        },
        data() {
            return {
                notes: this.notes
            }
        },
        created: function () {
            this.fetchNotes();
        },
        methods: {
            fetchNotes: function () {
                this.notes = [
                    {
                        _id: "1",
                        title: "tile1",
                        desc: "axy"
                    },
                    {
                        _id: "2",
                        title: "pqr",
                        desc: "kdkd"
                    }
                ]
            }
        }
    }

</script>
<style>
    [v-cloak] {
        display: none;
    }
</style>
