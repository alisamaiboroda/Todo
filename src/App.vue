<template>
  <div id="app" class="container">
    <h1>Todo application</h1>
    <AddTodo @add-todo="addTodo" />
    <div class="select">
      <a-select
        v-model="filter"
        default-value="all"
        style="width: 600px"
        @change="handleChange"
      >
        <a-select-option value="all"> All </a-select-option>
        <a-select-option value="completed"> Completed </a-select-option>
        <a-select-option value="not-completed"> Not Completed </a-select-option>
      </a-select>
    </div>
    <TodoList
      v-if="filteredTodos.length"
      v-bind:todos="filteredTodos"
      @remove-todo="removeTodo"
    />
    <p v-else>No todos!</p>
  </div>
</template>

<script>
import TodoList from "./components/TodoList";
import AddTodo from "./components/AddTodo";

export default {
  name: "App",
  data() {
    return {
      todos: [
        { id: 1, title: "Купить хлеб", completed: false },
        { id: 2, title: "Накормить кота", completed: false },
        { id: 3, title: "Купить корм для кота", completed: false },
      ],
      filter: "all",
    };
  },
  computed: {
    filteredTodos() {
      if (this.filter === "all") {
        return this.todos;
      }
      if (this.filter === "completed") {
        return this.todos.filter((t) => t.completed);
      }
      if (this.filter === "not-completed") {
        return this.todos.filter((t) => !t.completed);
      } else {
        return this.todos;
      }
    },
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter((t) => t.id !== id);
    },
    addTodo(todo) {
      this.todos.push(todo);
    },
  },
  components: {
    TodoList,
    AddTodo,
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
.select {
  margin-bottom: 1rem;
}
</style>
