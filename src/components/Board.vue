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
          :columnState="'todo'"
          v-on:update:selectedId="select"
          v-on:deleteTodo="deleteTodo"
          v-on:changeState="changeState"
        />
        <column
          :todos="inProgressList"
          :selectedId="selectedId"
          :columnState="'inProgress'"
          v-on:update:selectedId="select"
          v-on:deleteTodo="deleteTodo"
          v-on:changeState="changeState"
        />
        <column
          class="right"
          :todos="doneList"
          :selectedId="selectedId"
          :columnState="'done'"
          v-on:update:selectedId="select"
          v-on:deleteTodo="deleteTodo"
          v-on:changeState="changeState"
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
          body: "todo task 1 body",
          state: STATE_TODO
        },
        {
          id: 1,
          title: "todo2",
          body: "todo task 2 body",
          state: STATE_IN_PROGRESS
        },
        {
          id: 2,
          title: "todo3",
          body:
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
          state: STATE_DONE
        }
      ]
    };
  },
  methods: {
    select: function(id) {
      this.selectedId = id;
    },
    addTodo: function(title, body) {
      console.log(`board adding ${title} ${body}`);
      this.todos.push({
        id: this.todos.length + 1,
        title: title,
        body: body,
        state: STATE_TODO
      });
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
    },
    changeState: function(strId, state) {
      let id = parseInt(strId);
      this.todos
        .filter(todo => todo.id === id)
        .forEach(todo => {
          console.log(`changin state of ${id} to ${state}`);
          todo.state = state;
        });
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