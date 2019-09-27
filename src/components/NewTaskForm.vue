<template>
  <section class="new-task-form">
    <H2>NEW TODO</H2>
    <button class="close-button btn btn-secondary" v-on:click="close">close</button>
    <div class="form-group">
      <label for="title">Title:</label>
      <input id="title" type="text" v-model="title" class="form-control" />
    </div>
    <div class="form-group">
      <label for="body">Body:</label>
      <input id="body" type="text" v-model="body" class="form-control" />
    </div>
    <button v-on:click="save" class="btn btn-primary">save</button>
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
  width: 50%;
  position: fixed; /* or absolute */
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  text-align: left;
}
.close-button {
  position: absolute;
  right: 10px;
  top: 10px;
}
</style>