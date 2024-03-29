<template>
  <div>
    <ControlPanel/>
  </div>
  <div class="main" v-for="todo in todos" :key="todo.id">
    <ToDo :title="todo.title" :details="todo.details"/>
  </div>
</template>

<script >
import ToDo from './components/ToDo';
import ControlPanel from './components/ControlPanel';
  export default {
    data(){
      return{
        todos: []
      }
    },
    mounted(){
     fetch("http://localhost:3000/todos")
     .then(res => res.json())
     .then(data => this.todos = data)
    }
  }
</script>

<style lang="scss" scoped>

</style>