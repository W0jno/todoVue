<template>
  <div class="container">
    <div v-show="!isEditing" class="title">{{ title }}</div>
    <input
      v-show="isEditing"
      type="text"
      class="title"
      placeholder="Change title"
      v-model="titleEdit"
    />
    <div class="w-3/12">
      <NuxtLink :to="`/${this.id}`">
        <button class="btn bg-blue-400 w-1/3">Details</button>
      </NuxtLink>
      <button
        v-show="!isEditing"
        class="btn bg-yellow-400 w-1/3"
        @click="editHandler"
      >
        Edit
      </button>

      <button
        v-show="isEditing"
        class="btn bg-green-500 w-1/3"
        @click="editHandler"
      >
        Apply
      </button>

      <button class="btn w-1/3" @click="deleteHandler">Delete</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ToDo",
  data() {
    return {
      title: "",
      isEditing: false,
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
    async editHandler() {
      try {
        this.isEditing = !this.isEditing;
        const res = await $fetch(`http://localhost:3000/todos/${this.id}`, {
          method: "PUT",
          body: {
            title: this.titleEdit,
            details: this.details,
          },
        });
        this.$emit("todoEdited", res);
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
