# 波浪悬浮球

<floatingBall/>

```vue
<template>
  <div class="floating-container">
    <div
      class="container"
      :class="{ warning: parseInt(usingRate) > 60, danger: parseInt(usingRate) > 80 }"
    >
      <div class="wave"></div>
      <div class="wave-mask" :style="`top: ${40 - parseInt(usingRate)}px`"></div>
    </div>
    <div class="using-slider">
      <span>使用率：{{usingRate}} %</span>
      <el-slider v-model="usingRate"></el-slider>
    </div>
  </div>
</template>

<script>
export default {
  name: "floatingBall",
  data() {
    return {
      usingRate: 30
    };
  }
};
</script>

<style lang="scss" scoped>
.floating-container{
    position: relative;
    height: 280px;
}
.container {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  border: 3px solid #67c23a;
  background: #ffffff;
  overflow: hidden;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  padding: 5px;
  .wave {
    position: relative;
    width: 100px;
    height: 100px;
    background-image: linear-gradient(-180deg, #aaff80 13%, #67c23a 91%);
    border-radius: 50%;
  }
  .wave-mask {
    position: absolute;
    width: 200px;
    height: 200px;
    top: 0;
    left: 50%;
    border-radius: 40%;
    background-color: rgba(255, 255, 255, 0.9);
    transform: translate(-50%, -70%) rotate(0);
    animation: toRotate 10s linear -5s infinite;
    z-index: 20;
  }
  &.warning {
    border: 3px solid #e6a23c;
    .wave {
      background-image: linear-gradient(-180deg, #f0c78a 13%, #e6a23c 91%);
    }
    &.danger {
      border: 3px solid #f56c6c;
      .wave {
        background-image: linear-gradient(-180deg, #f78989 13%, #f56c6c 91%);
      }
    }
  }
}
.using-slider {
  width: 400px;
  margin: 0 auto;
}

@keyframes toRotate {
  50% {
    transform: translate(-50%, -70%) rotate(180deg);
  }
  100% {
    transform: translate(-50%, -70%) rotate(360deg);
  }
}
</style>

```