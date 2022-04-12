<template>
  <div class="progress-bar">
    <span> {{ percetage }}% </span>
    <div class="progress-percent" :style="{width: percetage + '%'}"></div>
  </div>
</template>

<script>
export default {
  props: {
    tasks: Array,
  },
  data() {
    return { counting: 0 };
  },
  computed: {
    percetage() {
      const length = this.tasks.length;
      if(length === 0) return 0
      const test = this.tasks.filter(task => task.done === true).length;
      return Math.round((test / length) * 100);
    },
  },
};
</script>

<style scoped>
span {
  position: absolute;
  top: 25%;
  left: 50%;
  font-size: 18px;
  font-weight: 600;
}
.progress-bar {
  position: relative;
  width: 70%;
  border: 1px solid #fff;
  border-radius: 5px;
  overflow: hidden;
  min-height: 45px;
}
.progress-percent {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  background: #26de81;
}
</style>
