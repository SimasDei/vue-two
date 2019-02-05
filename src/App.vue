<template>
  <div id="app">
    <Header/>
    <section class="todo__section">
      <AddTodo v-on:add-todo="addTodo"/>
      <Todo v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
    </section>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
import Todo from "./components/Todo";
import AddTodo from "./components/AddTodo";
import Header from "./components/layout/Header";
import axios from "axios";

export default {
  name: "app",
  components: {
    Todo,
    Header,
    AddTodo
  },
  data() {
    return {
      todos: []
    };
  },
  methods: {
    deleteTodo(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(
          response => (this.todos = this.todos.filter(todo => todo.id !== id))
        )
        .catch(error => console.log(error));
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;
      axios
        .post("https://jsonplaceholder.typicode.com/todos", {
          title,
          completed
        })
        .then(response => (this.todos = [...this.todos, response.data]))
        .catch(error => console.log(error));
    }
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=8")
      .then(response => (this.todos = response.data))
      .catch(error => console.log(error));
  }
};
</script>

<style>
html {
  background: #333;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.todo__section {
  max-width: 80%;
  margin: auto;
}
.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover,
.btn:active {
  background: #666;
}
</style>
