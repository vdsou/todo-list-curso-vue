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
      const deletedTask = this.tasks.filter((task) => task.id !== id);
      this.$emit("updateTask", [...deletedTask]);
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
  display: flex;
  justify-content: center;
  width: 100%;
  padding: 15px;
}
.tasks ul {
  margin: 0;
  padding: 0;
  width: 80%;
  height: 100%;
  display: flex;
  justify-content: center;
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
  margin: 5px;
  padding: 5px;
  border-radius: 5px;
  transform: scale(0.99);
}
.tasks ul li.done {
  background: #2d98da;
}
.tasks ul li .text {
  word-wrap: break-word;
  width: 100%;
  text-align: center;
  padding: 0 10px;
  overflow-y: auto;
}
.tasks ul li.done .text {
  text-decoration: line-through;
}
.tasks ul li:hover,
.tasks ul li.done:hover {
  transform: scale(1);
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
  font-weight: 600;
  font-size: 13px;
  border: none;
  border-radius: 5px;
  background: #d1d8e0;
}
.tasks button:hover {
  color: #2d98da;
}
</style>
