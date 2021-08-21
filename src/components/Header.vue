<template>
  <header>
    <h1>{{ Title }}</h1>
    <Button
      @toggle-addTask="$emit('toggle-addTask')"
      :text="showAddTasks ? 'Close' : 'Add Task'"
      :color="showAddTasks ? 'red' : 'green'"
    />
  </header>
</template>

<script>
import Button from "./Button.vue";
export default {
  name: "Header",
  props: {
    Title: {
      type: String,
      default: "",
    },
    showAddTasks: Boolean,
  },
  components: {
    Button,
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>
