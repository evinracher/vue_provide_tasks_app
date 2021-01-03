<template>
  <form class="my-3" @submit.prevent="addTask">
    <input
      class="form-control my-2"
      type="text"
      placeholder="Enter a task"
      v-model.trim="text"
    />
    <button class="btn btn-primary w-100" type="submit">Add</button>
  </form>
</template>

<script>
import { inject, ref } from "vue";
export default {
  setup() {
    const text = ref("");
    const tasks = inject("tasks");
    const addTask = () => {
      if (text.value === "") {
        return console.log("Empty text");
      }
      const task = {
        text: text.value,
        state: false,
        id: Date.now(),
      };
      tasks.value.push(task);
      text.value = "";
    };

    return { text, addTask };
  },
};
</script>

<style>
</style>