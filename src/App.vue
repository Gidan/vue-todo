<template>
  <div id="app">
    <img class="vue-logo" alt="Vue logo" src="./assets/logo.png" />
    <img alt="Todo logo" src="./assets/todo.png" />
    <board />
  </div>
</template>

<script>
import board from "./components/Board.vue";

export default {
  name: "app",
  components: {
    board
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.vue-logo {
  max-width: 100px;
  object-fit: scale-down;
}
</style>
