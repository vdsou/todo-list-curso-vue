<template>
  <form action="" class="new-task-form">
    <input type="text" placeholder="Nova tarefa?" />
    <button>+</button>
  </form>
</template>

<script>
export default {};
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
}
button {
  font-size: 18px;
  cursor: pointer;
  width: 10%;
  border: none;
  height: 100%;
}
</style>
