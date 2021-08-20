<template>
  <header>
    <h1>{{ Title }}</h1>
    <Button
      @toggle-addTask="$emit('toggle-addTask')"
      :text="showAddTask ? 'Close' : 'Add Task'"
      :color="showAddTask ? 'red' : 'green'"
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
      showAddTask: Boolean,
    },
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
