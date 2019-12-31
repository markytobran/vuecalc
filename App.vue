<template>
  <div id="app">
    <calc></calc>
  </div>
</template>

<script>
import calc from "./Calc";
export default {
  name: "app",
  data() {
    return {
      msg: "Welcome to Your Vue.js App"
    };
  },
  components: {
    calc: calc
  }
};
</script>

<style>
body {
  background-image: linear-gradient(45deg, red, blue);
  background-repeat: no-repeat;
  height: 100vh;
  display: flex;
  text-align: center;
  justify-content: center;
  align-items: center;
}
</style>
