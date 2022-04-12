<template>
  <form @submit.prevent="addTask" class="new-task-form">
    <input type="text" placeholder="Nova tarefa" v-model="text" />
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
      let checkTask = this.tasks.filter((task) => task.text === this.text);
      if (this.text === "") checkTask = 0;
      if (checkTask.length === 0) {
        this.tasks.push(this.task);
      }
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
  width: 50%;
}
input {
  opacity: 0.9;
  font-size: 18px;
  width: 90%;
  height: 100%;
  border: none;
  overflow: hidden;
  padding: 15px;
  outline: none;
}
::placeholder{
  color: #778ca3;
}
.new-task-form:hover input {
  opacity: 1;
}
button {
  font-size: 18px;
  cursor: pointer;
  width: 10%;
  border: none;
  height: 100%;
  background: #a5b1c2;
  font-size: 18px;
  font-weight: 600;
  color: #fff;
}
button:hover {
  color: #d1d8e0;
}
</style>
