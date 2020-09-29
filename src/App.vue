<template>
  <div id="app">
    <Stopwatch />
  </div>
</template>

<script>
import Stopwatch from "./components/Stopwatch.vue";

export default {
  name: "App",
  components: {
    Stopwatch,
  },
};
</script>

<style>
html {
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: inherit;
  margin: 0;
  padding: 0;
}

#app {
  min-height: 100vh;
  background-color: #353638;
}
</style>
