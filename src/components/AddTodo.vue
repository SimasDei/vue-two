<template>
  <div>
    <form @submit="addTodo">
      <input type="text" name="title" v-model="title" placeholder="Add Task">
      <input type="submit" value="Create" class="btn">
    </form>
  </div>
</template>

<script>
import uuid from "uuid";
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      const newTodo = {
        id: uuid.v4(),
        title: this.title,
        completed: false
      };
      // Hoist up to parent
      this.$emit("add-todo", newTodo);
      // Clear input
      this.title = "";
    }
  }
};
</script>

<style scoped>
form {
  display: flex;
}

input[type="text"] {
  flex: 10;
  padding: 5px;
}

input[type="submit"] {
  flex: 2;
}
</style>

