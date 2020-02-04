<template>
    <div>
        <h1>{{header}}</h1>
    </div>
</template>
<script>
    export default {
        props: ['header'],
        data: {
            values: [
                {
                    _id: "1"
                }
            ]
        }
    }
</script>
