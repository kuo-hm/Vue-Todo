<template>
  <div :key="task.id" v-for="task in tasks">
    <Task
      :task="task"
      @toggle-reminder="$emit('toggle-reminder', task.id)"
      @delete="$emit('delete', task.id)"
    />
  </div>
</template>

<script>
import Task from "./Task.vue";
export default {
  name: "Tasks",
  props: {
    tasks: Array,
  },
  components: {
    Task,
  },
  emits: ["delete", "toggle-reminder"],
};
</script>

<style></style>
