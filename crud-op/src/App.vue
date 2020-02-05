<template>
    <div id="app">
        <h2>Welcome</h2>
        <Notes v-bind:notes="notes"></Notes>

    </div>
</template>

<script>
    import Notes from './components/Notes'
    import axios from 'axios'

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
                var url = 'https://arun-express-api.herokuapp.com/posts';
                axios.get(url)
                    .then(res => {
                        this.notes = res.data
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
