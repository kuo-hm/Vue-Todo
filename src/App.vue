<template>
  <div class="container">
    <Header />
    <Tasks
      :tasks="taskes"
      @toggle-reminder="toggleReminder"
      @delete="deleteTask"
    />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";
export default {
  name: "App",
  components: {
    Header,
    Tasks,
  },
  data() {
    return {
      taskes: [],
    };
  },
  methods: {
    toggleReminder(task) {
      this.taskes = this.taskes.map((t) => {
        if (t.id === task) {
          t.reminder = !t.reminder;
        }
        return t;
      });
    },
    deleteTask(id) {
      if (confirm("Are you sure?")) {
        this.taskes = this.taskes.filter((task) => task.id !== id);
      }
    },
  },
  created() {
    this.taskes = [
      {
        id: 1,
        title: "Buy groceries",
        day: "Monday",
        reminder: true,
      },
      {
        id: 2,
        title: "Learn Vue",
        day: "Tuesday",
        reminder: false,
      },
      {
        id: 3,
        title: "Write code",
        day: "Wednesday",
        reminder: false,
      },
      {
        id: 4,
        title: "Do taxes",
        day: "Thursday",
        reminder: true,
      },
    ];
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Poppins", sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
