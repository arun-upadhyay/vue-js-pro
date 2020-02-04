<template>
    <div id="app">
        <Notes header='CRUD Operations'></Notes>
    </div>
</template>

<script>
    import Notes from "./components/notes"

    export default {
        name: "app",
        components: {
            Notes
        },
        data: {
            message: "hell world"
        }
        ,
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
