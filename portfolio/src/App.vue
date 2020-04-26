<template>
  <div id="app">
    <Portfolio />
  </div>
</template>

<script>
import Portfolio from "./components/Portfolio";

export default {
  name: "App",
  components: {
    Portfolio
  }
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background-color: black;
}
</style>
