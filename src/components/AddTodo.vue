<template>
  <a-form class="form" @submit.prevent="onSubmit">
    <a-input
      class="add-input"
      placeholder="Create new task..."
      v-model="title"
    ></a-input>
    <a-button type="primary" html-type="submit"> Create </a-button>
  </a-form>
</template>

<script>
export default {
  data() {
    return {
      title: "",
    };
  },
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          completed: false,
        };
        this.$emit("add-todo", newTodo);
        this.title = "";
      }
    },
  },
};
</script>

<style scoped>
.form {
  margin-bottom: 1rem;
}
.add-input {
  width: 530px;
}
</style>