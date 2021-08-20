<template>
  <header>
    <h1>{{ Title }}</h1>
    <Button text="Add" color="#F8BBD0" />
  </header>
</template>

<script>
import Button from "./Button.vue";
export default {
  name: "header",
  props: {
    Title: {
      type: String,
      default: "Task Tracker",
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
