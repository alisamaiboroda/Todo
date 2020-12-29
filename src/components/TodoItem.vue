<template>
  <li>
    <span>
      <input type="checkbox" />
      <strong>{{ todo.id }}</strong>
      {{ todo.title }}
    </span>
    <button class="rm">&times;</button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped>
li {
  border: 1px solid #cccccc;
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
}
.done {
  text-decoration: line-through;
}
</style>