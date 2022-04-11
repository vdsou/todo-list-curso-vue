<template>
  <form @submit.prevent="addTask" class="new-task-form">
    <input type="text" placeholder="Nova tarefa?" v-model="text" />
    <button>+</button>
  </form>
</template>

<script>
export default {
  props: {
    tasks: Array,
  },
  data() {
    return {
      task: {
        id: 0,
        text: "",
        done: false,
      },
      text: "",
    };
  },
  methods: {
    addTask() {
      const id = Math.round(Math.random() * 9999);
      this.task.id = id;
      this.task.text = this.text;
      this.task.done = false;
      this.tasks.push(this.task);
      this.task = {};
      this.text = "";

      this.$emit("addTask", this.tasks);
    },
  },
};
</script>

<style scoped>
.new-task-form {
  margin: 20px 0;
  border: 1px solid #fff;
  display: flex;
  width: 400px;
}
input {
  font-size: 18px;
  width: 90%;
  height: 100%;
  border: none;
  overflow: hidden;
  padding: 15px;
  outline: none;
}
button {
  font-size: 18px;
  cursor: pointer;
  width: 10%;
  border: none;
  height: 100%;
}
</style>
