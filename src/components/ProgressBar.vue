<template>
  <div class="progress-bar">
    <span> 100% </span>
    <div class="progress-percent"></div>
  </div>
</template>

<script>
export default {};
</script>

<style>
span {
  position: absolute;
  top: 10%;
  left: 49%;
  font-size: 18px;
  font-weight: 600;
}
.progress-bar {
  position: relative;
  width: 70%;
  border: 1px solid #fff;
  border-radius: 5px;
  overflow: hidden;
  height: 30px;
}
.progress-percent {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  /* width: 0%; */
  background: #26de81;
}
</style>
