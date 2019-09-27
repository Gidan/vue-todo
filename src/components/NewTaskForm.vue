<template>
  <section class="new-task-form">
    <H2>NEW TODO</H2>
    <button class="close-button" v-on:click="close">close</button>

    <div class="field">
      <label for="title">Title:</label>
      <input id="title" type="text" v-model="title" />
    </div>
    <div class="field">
      <label for="body">Body:</label>
      <input id="body" type="text" v-model="body" />
    </div>

    <button v-on:click="save">save</button>
  </section>
</template>

<script>
export default {
  name: "newTaskForm",
  data: function() {
    return {
      title: null,
      body: null,
      state: "todo"
    };
  },
  methods: {
    save: function() {
      this.$emit("add:todo", this.title, this.body);
    },
    close: function() {
      this.$emit("update:closeNewTaskForm");
    }
  }
};
</script>

<style scoped>
.new-task-form {
  background: white;
  padding: 20px;
  border: 1px;
  border-color: black;
  border-style: solid;
  width: 50%;
  position: fixed; /* or absolute */
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.field label {
  width: 20%;
  text-align: left;
}
.field input {
  width: 80%;
}
.close-button {
  position: absolute;
  right: 10px;
  top: 10px;
}
</style>