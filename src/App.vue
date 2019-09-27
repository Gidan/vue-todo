<template>
  <div id="app">
    <img class="vue-logo" alt="Vue logo" src="./assets/logo.png" />
    <img alt="Todo logo" src="./assets/todo.png" />
    <img class="new-task-button" alt="newTask" src="./assets/add.png" v-on:click="openNewTaskForm" />
    <board ref="board" />
    <newTaskForm
      v-if="showNewTaskForm"
      v-on:add:todo="addTodo"
      v-on:update:closeNewTaskForm="closeNewTaskForm"
    />
  </div>
</template>

<script>
import board from "./components/Board.vue";
import newTaskForm from "./components/NewTaskForm.vue";

export default {
  name: "app",
  components: {
    board,
    newTaskForm
  },
  data: function() {
    return {
      showNewTaskForm: false
    };
  },
  methods: {
    addTodo: function(title, body) {
      this.$refs.board.addTodo(title, body);
      this.closeNewTaskForm();
    },
    closeNewTaskForm: function() {
      this.showNewTaskForm = false;
    },
    openNewTaskForm: function() {
      this.showNewTaskForm = true;
    }
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
.new-task-button {
  position: fixed;
  bottom: 20px;
  right: 20px;
  max-width: 70px;
}
</style>
