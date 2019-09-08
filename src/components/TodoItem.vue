<template>
  <div>
    <h2>{{ todo.message }}</h2>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: {
    todo: Object
  }
};
</script>

<style scoped>
div {
  width: 100%;
  background: rgb(255, 255, 255);
  border-width: 0px 0px 1px 0px;
  border-color: rgb(206, 206, 206);
  border-style: solid;
  padding: 8px;
}
h2 {
  margin: 0px;
}
</style>