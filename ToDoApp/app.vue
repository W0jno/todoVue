<template>
  <div>
    <ControlPanel @todoAdded="handleTodoAdded" />
  </div>
  <div class="main" v-for="todo in todos" :key="todo.id">
    <ToDo
      :title="todo.title"
      :details="todo.details"
      :id="todo.id"
      @todoDeleted="handleToDoDeleted"
    />
  </div>
</template>

<script>
import ToDo from "./components/ToDo";
import ControlPanel from "./components/ControlPanel";
export default {
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    handleTodoAdded(newTodo) {
      this.todos.push(newTodo);
    },
    handleToDoDeleted() {
      this.fetchData();
    },
    fetchData() {
      fetch("http://localhost:3000/todos")
        .then((res) => res.json())
        .then((data) => (this.todos = data));
    },
  },
  mounted() {
    this.fetchData();
  },
};
</script>

<style lang="scss" scoped></style>
