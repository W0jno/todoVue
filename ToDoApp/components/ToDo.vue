<template>
    <div class="container ">
        <div class="content">{{ content }}</div>
        <button class="btn">Delete</button>
    </div>
</template>

<script>
    export default {
        name: "ToDo",
    data(){
        return{
            content: "brauwrka",
            delete: "",
            isDone: false
        }
    },
    methods: {
        increment () {
            this.count++;
        }
    }
    }
</script>

<style  scoped>

</style>