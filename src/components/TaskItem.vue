<template>
  <div
    class="alert alert-warning mt-3 d-flex justify-content-between alig-items-center"
  >
    <p class="m-0" :class="{ marked: task.state }">{{ task.text }}</p>
    <div>
      <i
        class="fas mx-2"
        :class="[
          task.state ? 'fa-undo-alt text-dark' : 'fa-check-circle text-success',
        ]"
        role="button"
        @click="modifyTask(task.id)"
      ></i>
      <i
        class="fas fa-minus-circle text-danger"
        role="button"
        @click="deleteTask(task.id)"
      ></i>
    </div>
  </div>
</template>

<script>
import { inject } from "vue";
export default {
  props: {
    task: {
      type: Object,
      required: true,
    },
  },
  setup() {
    const tasks = inject("tasks");

    const deleteTask = (id) => {
      tasks.value = tasks.value.filter((item) => item.id !== id);
    };
    const modifyTask = (id) => {
      tasks.value = tasks.value.map((item) =>
        item.id === id ? { ...item, state: !item.state } : item
      );
    };
    return { deleteTask, modifyTask };
  },
};
</script>

<style scoped>
.marked {
  text-decoration: line-through;
}
</style>