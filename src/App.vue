<template>
  <div id="app">
    <h1>Tarefas</h1>
    <ProgressBar :tasks="tasks" />
    <NewTask :tasks="tasks" @addTask="tasks = $event" />
    <Tasks :tasks="tasks" @updateTask="tasks = $event" />
  </div>
</template>

<script>
import ProgressBar from "@/components/ProgressBar.vue";
import Tasks from "@/components/Tasks.vue";
import NewTask from "@/components/NewTask.vue";

export default {
  components: { ProgressBar, NewTask, Tasks },
  data() {
    return {
      tasks: [],
    };
  },
  watch: {
    tasks() {
      localStorage.setItem("tasks", JSON.stringify(this.tasks));
    },
  },
  created() {
    const tasks = localStorage.getItem("tasks");
    if (tasks) {
      this.tasks = JSON.parse(tasks);
    }
  },
  updated() {
    localStorage.setItem("tasks", JSON.stringify(this.tasks));
  },
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  transition: all ease 200ms;
}
body {
  font-family: "Lato", sans-serif;
  /* background: linear-gradient(to right, rgb(22, 34, 42), rgb(58, 96, 115)); */
  background: #4b79a1; /* fallback for old browsers */
  background: -webkit-linear-gradient(
    to right,
    #283e51,
    #4b79a1
  ); /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(
    to right,
    #283e51,
    #4b79a1
  ); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

  color: #fff;
}

#app {
  display: flex;
  flex: 1;
  flex-direction: column;
  align-items: center;
  height: 100vh;
}

#app h1 {
  margin-bottom: 15px;
  font-weight: 300;
  font-size: 2.5rem;
}
</style>
