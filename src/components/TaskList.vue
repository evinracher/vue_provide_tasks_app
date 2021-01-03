<template>
  <h3>Add task</h3>
  <TaskForm />
  <TaskItem v-for="task in tasks" :key="task.id" :task="task" />
  <div class="alert alert-dark mt-3" v-if="tasks.length === 0">
    Without tasks
  </div>
</template>

<script>
import { provide, ref, watchEffect } from "vue";
import TaskForm from "./TaskForm.vue";
import TaskItem from "./TaskItem.vue";
export default {
  components: { TaskForm, TaskItem },
  setup() {
    const tasks = ref([]);
    provide("tasks", tasks);
    const localTasks = localStorage.getItem("tasks");
    if (localTasks) {
      tasks.value = JSON.parse(localTasks);
    }
    watchEffect(() => {
      localStorage.setItem("tasks", JSON.stringify(tasks.value));
    });
    return { tasks };
  },
};
</script>

<style>
</style>