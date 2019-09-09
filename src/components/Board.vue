<template>
  <div>
    <div class="container">
      <div class="row">
        <h3 class="col-sm">TODO</h3>
        <h3 class="col-sm">IN PROGRESS</h3>
        <h3 class="col-sm">DONE</h3>
      </div>
      <div class="row">
        <column
          class="left"
          :todos="todoList"
          :selectedId="selectedId"
          v-on:update:selectedId="select"
          v-on:deleteTodo="deleteTodo"
        />
        <column
          :todos="inProgressList"
          :selectedId="selectedId"
          v-on:update:selectedId="select"
          v-on:deleteTodo="deleteTodo"
        />
        <column
          class="right"
          :todos="doneList"
          :selectedId="selectedId"
          v-on:update:selectedId="select"
          v-on:deleteTodo="deleteTodo"
        />
      </div>
    </div>
  </div>
</template>

<script>
import column from "./Column.vue";

const STATE_TODO = "todo";
const STATE_IN_PROGRESS = "inProgress";
const STATE_DONE = "done";

export default {
  name: "board",
  components: { column },
  data: function() {
    return {
      selectedId: 0,
      todos: [
        {
          id: 0,
          title: "todo1",
          body: "todo 1 body",
          state: STATE_TODO
        },
        {
          id: 1,
          title: "inprogress1",
          body: "in progress1 body",
          state: STATE_IN_PROGRESS
        },
        {
          id: 2,
          title: "done1",
          body:
            "Lorem ipsum, or lipsum as it is sometimes known, is dummy text used in laying out print, graphic or web designs. The passage is attributed to an unknown typesetter in the 15th century who is thought to have scrambled parts of Cicero's De Finibus Bonorum et Malorum for use in a type specimen book.",
          state: STATE_DONE
        }
      ]
    };
  },
  methods: {
    select: function(id) {
      this.selectedId = id;
    },
    deleteTodo: function(id) {
      let index = 0;
      for (let i = 0; i < this.todos.length; i++) {
        const t = this.todos[i];
        if (t.id === id) {
          this.$delete(this.todos, index);
          break;
        }
        index++;
      }
    }
  },
  computed: {
    todoList: function() {
      return this.todos.filter(todo => todo.state === STATE_TODO);
    },
    inProgressList: function() {
      return this.todos.filter(todo => todo.state === STATE_IN_PROGRESS);
    },
    doneList: function() {
      return this.todos.filter(todo => todo.state === STATE_DONE);
    }
  }
};
</script>

<style scoped>
</style>