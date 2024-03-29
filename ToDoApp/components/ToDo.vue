<template>
    <div class="container">
        <div class="title">{{ title }}</div> 
        <button class="btn">Delete</button>
    </div>
</template>

<script>
export default {
    name: "ToDo",
    data() {
        return {
            isDone: false
        };
    },
    props: {
        title: String,
        details: String,
    },

};
</script>
<style  scoped>

</style>