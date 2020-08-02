<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todoList" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from "./components/Todos";
import Header from "./components/layout/Header";
import AddTodo from "./components/AddTodo";
import axios from "axios";

export default {
  name: "App",
  components: {
    Todos,
    Header,
    AddTodo,
  },
  methods: {
    deleteTodo(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(
          () => (this.todoList = this.todoList.filter((todo) => todo.id !== id))
        )
        .catch((err) => console.log(err));

      // this.todoList = this.todoList.filter((t) => t.id !== id);
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;
      axios
        .post("https://jsonplaceholder.typicode.com/todos", {
          title: title,
          completed: completed,
        })
        .then((res) => (this.todoList = [...this.todoList, res.data]))
        .catch((err) => console.log(err));
      // this.todoList = [...this.todoList, newTodo];
    },
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=5")
      .then((res) => (this.todoList = res.data))
      .catch((err) => console.log(err));
  },
  data() {
    return {
      todoList: [],
    };
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}

.btn {
  display: inline-block;
  border: none;
  padding: 7px 20px;
  cursor: pointer;
  background-color: #555;
  color: #fff;
}
.btn:hover {
  background-color: #666;
}
</style>
