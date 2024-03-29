<template>
    <div class="main">
        <div class="container border-green-700">
            <div class="flex w-11/12">
                <input type="text" placeholder="Enter title" v-model="title"/>
                <input type="text" class="w-3/4"placeholder="Enter details" v-model="details"/>
            </div>
            <button class="btn bg-green-500">ADD</button>
        </div>
    </div>
    
</template>

<script>
    export default {
        data(){
            return{
                title: "",
                details: ""
            }
        },
        methods: {
            
        }
    }
</script>

<style lang="scss" scoped>

</style>