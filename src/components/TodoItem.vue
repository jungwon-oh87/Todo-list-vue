<template>
  <div class="todo-item" v-bind:class="{'completed':todoProp.completed}">
    <p>
      <input type="checkbox" v-on:change="toggleComplete" />
      {{todoProp.title}}
      <button @click="$emit('del-todo',todoProp.id)" class="del">x</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todoProp"],
  methods: {
    toggleComplete() {
      this.todoProp.completed = !this.todoProp.completed;
    },
  },
};
</script>

<style scoped>
.todo-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}

.completed {
  text-decoration: line-through;
}

.del {
  background: red;
  color: #fff;
  border: none;
  padding: 5px 10px;
  border-radius: 5px;
  cursor: pointer;
  float: right;
}
</style>