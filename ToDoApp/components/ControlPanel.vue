<template>
  <div class="main">
    <form class="container border-green-700" @submit.prevent="addTodo">
      <div class="flex w-11/12">
        <input
          type="text"
          placeholder="Enter title"
          name="title"
          v-model="title"
          required
        />
        <input
          type="text"
          class="w-3/4"
          name="details"
          placeholder="Enter details"
          v-model="details"
          required
        />
      </div>
      <button type="submit" class="btn bg-green-500">ADD</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "",
      details: "",
    };
  },
  methods: {
    async addTodo() {
      try {
        const res = await $fetch("http://localhost:3000/todos", {
          method: "POST",
          body: {
            title: this.title,
            details: this.details,
          },
        });

        this.title = "";
        this.details = "";
        await this.$emit("todoAdded", res);
      } catch (e) {
        console.error(e);
      }
    },
  },
};
</script>

<style lang="scss" scoped></style>
