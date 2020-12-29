<template>
  <li>
    <span v-bind:class="{ done: todo.completed }">
      <a-checkbox
        class="checkbox"
        v-on:change="todo.completed = !todo.completed"
      ></a-checkbox>

      <strong class="number">{{ index + 1 }}</strong>
      {{ todo.title }}
    </span>
    <button class="rm" v-on:click="$emit('remove-todo', todo.id)">
      &times;
    </button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
    index: Number,
  },
};
</script>

<style scoped>
li {
  border: 1px solid #cccccc;
  border-radius: 4px;
  display: flex;
  justify-content: space-between;
  padding: 0.5rem 0.2rem;
  margin-bottom: 1rem;
  width: 600px;
}
.rm {
  border-radius: 20%;
  border: none;
  color: white;
  background-color: #cccccc;
  font-weight: bold;
  margin-right: 1rem;
}
.number {
  margin-right: 1rem;
  margin-left: 1rem;
}
.checkbox {
  margin-left: 1rem;
}
.done {
  text-decoration: line-through;
}
</style>