<template>
  <header>
    <h1>{{ Title }}</h1>
    <Button
      v-show="homePage"
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
  computed: {
    homePage() {
      if (this.$route.path === "/") {
        return true;
      } else {
        return false;
      }
    },
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
