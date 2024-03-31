<template>
  <div v-if="todo">
    <p>Todo details: {{ todo.details }}</p>
  </div>
</template>

<script setup>
const { id } = useRoute().params;
const todos = ref([]);

async function fetchTodos() {
  try {
    const res = await fetch("http://localhost:3000/todos");
    const data = await res.json();
    todos.value = data;
  } catch (error) {
    console.error("Error fetching todos:", error);
  }
}

const todo = computed(() => todos.value.find((x) => x.id == id));

fetchTodos();
</script>

<style scoped></style>
