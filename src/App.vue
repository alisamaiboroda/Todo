<template>
  <div id="app" class="container">
    <h1>Todo application</h1>
    <TodoList v-bind:todos="todos" />
  </div>
</template>

<script>
import TodoList from "./components/TodoList";
export default {
  name: "App",
  data() {
    return {
      todos: [
        { id: 1, title: "Купить хлеб", completed: false },
        { id: 2, title: "Накормить кота", completed: false },
        { id: 3, title: "Купить корм для кота", completed: false },
      ],
    };
  },
  components: {
    TodoList,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.container {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
}
</style>
