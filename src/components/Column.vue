<template>
  <div class="col-sm column">
    <TodoItem v-for="todo in todos" :key="todo.id" :todo="todo" />
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";
export default {
  name: "column",
  components: { TodoItem },
  props: ["todos"]
};
</script>

<style scoped>
.column {
  /* width: 33%; */
  height: 70vh;
  background-color: rgb(228, 228, 228);
  border-color: rgb(109, 109, 109);
  border-style: solid;
  border-width: 1px;
  padding-left: 0;
  padding-right: 0;
  /* display: inline-block; */
  /* position: relative; */
}
.column.left {
  border-width: 1px 0px 1px 1px;
}
.column.right {
  border-width: 1px 1px 1px 0px;
}
</style>