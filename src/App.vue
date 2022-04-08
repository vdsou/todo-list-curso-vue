<template>
  <div id="app">
    <h1>Tarefas</h1>
    <ProgressBar />
    <NewTask />
    <Tasks />
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
};
</script>

<style>
* {
  box-sizing: border-box;
}
body {
  font-family: "Lato", sans-serif;
  background: linear-gradient(to right, rgb(22, 34, 42), rgb(58, 96, 115));
  color: #fff;
}

#app {
  display: flex;
  flex: 1;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

#app h1 {
  margin-bottom: 5px;
  font-weight: 300;
  font-size: 3rem;
}
</style>
