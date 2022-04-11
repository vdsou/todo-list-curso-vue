<template>
  <div class="tasks">
    <ul>
      <li v-for="task in list" :key="task.id" :class="{ done: task.done }">
        <h3 class="text">
          {{ task.text }}
        </h3>
        <div class="buttons">
          <button @click="remove(task.id)">Remover</button>
          <button @click="setStatus(task.id)">Feita</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Tasks",
  props: {
    tasks: Array,
  },
  data() {
    return { id: "" };
  },
  methods: {
    remove(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
    setStatus(id) {
      this.tasks.forEach((task) => {
        if (task.id === id) {
          return (task.done = !task.done);
        }
        return task.done;
      });
      this.$emit("updateTask", [...this.tasks]);
    },
  },
  computed: {
    list() {
      return this.tasks;
    },
  },
  watch: {
    tasks(value) {
      this.$emit("updateTask", value);
    },
  },
};
</script>

<style scoped>
.tasks {
  justify-content: center;
  width: 100%;
}
.tasks ul {
  margin: 10px auto;
  width: 100%;
  height: 100%;
  display: flex;
  flex-wrap: wrap;
}
.tasks ul li {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  list-style: none;
  background: #eb3b5a;
  height: 150px;
  width: 250px;
  margin: 15px;
  border-radius: 5px;
  transition: all ease 200ms;
}
.tasks ul li.done {
  background: #2d98da;
}
.tasks ul li.done .text {
  text-decoration: line-through;
}
.tasks ul li:hover,
.tasks ul li.done:hover {
  transform: scale(1.01);
}
.tasks .buttons {
  width: 100%;
  display: flex;
  justify-content: space-around;
}
.tasks button {
  cursor: pointer;
  padding: 5px 10px;
  color: #4b6584;
  font-weight: 500;
  font-size: 13px;
  border: none;
  border-radius: 5px;
  background: #d1d8e0;
  transition: ease all 200ms;
}
.tasks button:hover {
  /* background: #4b6584; */
  color: #2d98da;
}
</style>
