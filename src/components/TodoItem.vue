<template>
  <div class="todo-item" :class="{ 'selected':selected }" v-on:click="select">
    <h3>{{ todo.title }}</h3>
    <p>{{ todo.body }}</p>
    <div>
      <img src="../assets/delete.png" v-on:click="deleteTodo" />
      <img v-if="todo.state !== 'done'" src="../assets/play.png" v-on:click="promote" />
    </div>
  </div>
</template>

<script>
const next = {
  todo: "inProgress",
  inProgress: "done"
};

export default {
  name: "TodoItem",
  props: {
    todo: Object,
    selectedId: Number
  },
  methods: {
    select: function() {
      this.$emit("update:selectedId", this.todo.id);
    },
    deleteTodo: function() {
      this.$emit("deleteTodo", this.todo.id);
    },
    promote: function() {
      this.todo.state = next[this.todo.state];
    }
  },
  computed: {
    selected: function() {
      return this.selectedId === this.todo.id;
    }
  }
};
</script>s

<style scoped>
.todo-item {
  width: 100%;
  background: rgb(255, 255, 255);
  border-width: 0px 0px 1px 0px;
  border-color: rgb(206, 206, 206);
  border-style: solid;
  padding: 8px;
  text-align: left;
}
h3 {
  margin: 0px;
}
.selected {
  background: rgb(53, 211, 150);
}
</style>