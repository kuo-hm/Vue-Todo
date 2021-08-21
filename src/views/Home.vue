<template>
  <AddTask @addTask="addTask" v-show="showAddTask" />
  <Tasks
    :tasks="tasks"
    @toggle-reminder="toggleReminder"
    @delete="deleteTask"
  />
</template>

<script>
import Tasks from "../components/Tasks.vue";
import AddTask from "../components/AddTask.vue";
export default {
  name: "Home",
  components: {
    Tasks,
    AddTask,
  },
  props: {
    showAddTask: Boolean,
  },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    async toggleReminder(id) {
      const taskToToggle = await this.fetchTask(id);
      const updTask = { ...taskToToggle, reminder: !taskToToggle.reminder };
      const res = await fetch(`api/tasks/${id}`, {
        method: "PUT",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(updTask),
      });
      const data = await res.json();
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: data.reminder } : task
      );
    },
    async addTask(task) {
      const response = await fetch("/api/tasks", {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify(task),
      });
      const data = await response.json();
      this.tasks = [...this.tasks, data];
    },
    async fetchTasks() {
      const response = await fetch("api/tasks");
      const tasks = await response.json();
      return tasks;
    },
    async deleteTask(id) {
      if (confirm("Are you sure?")) {
        const response = await fetch(`api/tasks/${id}`, { method: "DELETE" });
        response.status === 200
          ? (this.tasks = this.tasks.filter((task) => task.id !== id))
          : alert("Error");
      }
    },
    async fetchTask(id) {
      const response = await fetch(`api/tasks/${id}`);
      const tasks = await response.json();
      return tasks;
    },
  },
  async created() {
    this.tasks = await this.fetchTasks();
  },
};
</script>

<style></style>
