<template>
  <div class="col-sm column">
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
  props: ["todos", "selectedId"],
  methods: {
    select: function(id) {
      this.$emit("update:selectedId", id);
    },
    deleteTodo: function(id) {
      this.$emit("deleteTodo", id);
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