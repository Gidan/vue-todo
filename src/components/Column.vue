<template>
  <div
    class="col-sm column"
    v-on:drop="drop($event)"
    v-on:dragover="allowDrop($event)"
    v-on:dragenter="dragenter"
  >
    <TodoItem
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      :selectedId="selectedId"
      v-on:update:selectedId="select"
      v-on:deleteTodo="deleteTodo"
    />
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";
export default {
  name: "column",
  components: { TodoItem },
  props: ["todos", "selectedId", "columnState"],
  methods: {
    select: function(id) {
      this.$emit("update:selectedId", id);
    },
    deleteTodo: function(id) {
      this.$emit("deleteTodo", id);
    },
    drop: function(ev) {
      event.preventDefault();
      let todoId = event.dataTransfer.getData("todoId");
      console.log("drop on column " + todoId);
      this.$emit("changeState", todoId, this.columnState);
    },
    allowDrop: function(ev) {
      event.preventDefault();
    },
    dragenter: function(ev) {
      console.log("drag enter column");
    }
  }
};
</script>

<style scoped>
.column {
  min-height: 100vh;
  background-color: rgb(228, 228, 228);
  border-color: rgb(109, 109, 109);
  border-style: solid;
  border-width: 1px;
  padding-left: 0;
  padding-right: 0;
}
.column.left {
  border-width: 1px 0px 1px 1px;
}
.column.right {
  border-width: 1px 1px 1px 0px;
}
</style>