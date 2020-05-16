<template>
  <div id="app">
    <Slider />
  </div>
</template>

<script>
import Slider from "./components/Slider";

export default {
  name: "App",
  components: {
    Slider: Slider
  }
};
</script>

<style>
@import "./App.css";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  width: 100%;
  height: 100%;
}
</style>
