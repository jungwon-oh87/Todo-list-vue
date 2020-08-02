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

export default {
  name: "App",
  components: {
    Todos,
    Header,
    AddTodo,
  },
  methods: {
    deleteTodo(id) {
      this.todoList = this.todoList.filter((t) => t.id !== id);
    },
    addTodo(newTodo) {
      this.todoList = [...this.todoList, newTodo];
    },
  },
  data() {
    return {
      todoList: [
        {
          id: 1,
          title: "finish vue hello world",
          completed: false,
        },
        {
          id: 2,
          title: "statsbot integration",
          completed: false,
        },
        {
          id: 3,
          title: "dish wash",
          completed: false,
        },
      ],
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
