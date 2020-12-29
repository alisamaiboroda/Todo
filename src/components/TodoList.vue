<template>
  <ul>
    <TodoItem v-for="todo in todos" v-bind:todo="todo" v-bind:key="todo" />
  </ul>
</template>

<script>
import TodoItem from "./TodoItem";
export default {
  props: ["todos"],
  components: {
    TodoItem,
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
</style>