<template>
  <div class="container">
    <div class="title">{{ title }}</div>
    <button class="btn" @click="deleteHandler">Delete</button>
  </div>
</template>

<script>
export default {
  name: "ToDo",
  data() {
    return {
      isDone: false,
    };
  },
  methods: {
    async deleteHandler() {
      try {
        const res = await $fetch(`http://localhost:3000/todos/${this.id}`, {
          method: "DELETE",
        });
        this.$emit("todoDeleted", res);
      } catch (e) {
        console.error(e);
      }
    },
  },
  props: {
    title: String,
    details: String,
    id: String,
  },
};
</script>
<style scoped></style>
