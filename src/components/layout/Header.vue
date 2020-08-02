<template>
  <header class="header">
    <h1>ToDoList</h1>
    <div class="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style scoped>
.header {
  background-color: #333;
  color: #fff;
  text-align: center;
  padding: 10px;
}

.nav {
  padding: 10px;
}

.nav a {
  font-weight: bold;
  /* color: #2c3e50; */
  color: #fff;
  text-decoration: none;
}

.nav a.router-link-exact-active {
  color: #42b983;
}
</style>
