<template>
  <div id="app">
    <h1>Welcome to To Do List App</h1>
    <Todos v-bind:todos="todoList" />
  </div>
</template>

<script>
import Todos from "./components/Todos";

export default {
  name: "App",
  components: {
    Todos,
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
          completed: true,
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
</style>
