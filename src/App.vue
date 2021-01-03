<template>
  <h1 class="text-center">Task App</h1>
  <p class="text-center">Created by evinracher</p>
  <div class="container mt-4">
    <TaskList />
  </div>
</template>

<script>
import TaskList from "./components/TaskList.vue";
export default {
  name: "App",
  components: { TaskList },
};
</script>