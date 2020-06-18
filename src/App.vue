<template>
  <div id="app">
    <div class="container">
      <AddTodo/>
      <FilterTodo/>
      <Todos/>
    </div>
  </div>
</template>

<script>
import Todos from "./components/Todos.vue";
import AddTodo from "./components/AddTodo.vue";
import FilterTodo from "./components/FilterTodo.vue";

export default {
  name: "app",
  components: {
    Todos,
    AddTodo,
    FilterTodo
  }
};
</script>

<style>
body {
  line-height: 1.6;
  background: #e8f7f0;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.container {
  max-width: 1110px;
  margin: auto;
  overflow: auto;
  padding: 0 2rem;
}
</style>
