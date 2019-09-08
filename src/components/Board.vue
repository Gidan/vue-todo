<template>
  <div>
    <div class="container">
      <div class="row">
        <h3 class="col-sm">TODO</h3>
        <h3 class="col-sm">IN PROGRESS</h3>
        <h3 class="col-sm">DONE</h3>
      </div>
      <div class="row">
        <column class="left" :todos="todoList" />
        <column :todos="inProgressList" />
        <column class="right" :todos="doneList" />
      </div>
    </div>
  </div>
</template>

<script>
import column from "./Column.vue";
export default {
  name: "board",
  components: { column },
  data: function() {
    return {
      todos: [
        {
          id: 0,
          message: "todo1",
          state: "0"
        },
        {
          id: 1,
          message: "todo1",
          state: "1"
        },
        {
          id: 2,
          message: "todo1",
          state: "2"
        }
      ]
    };
  },
  computed: {
    todoList: function() {
      return this.todos.filter(todo => todo.state === "0");
    },
    inProgressList: function() {
      return this.todos.filter(todo => todo.state === "1");
    },
    doneList: function() {
      return this.todos.filter(todo => todo.state === "2");
    }
  }
};
</script>

<style scoped>
</style>