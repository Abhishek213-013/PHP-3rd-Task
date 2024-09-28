<template>
  <li :class="{ completed: todo.completed }">
    {{ todo.text }}
    <button @click="toggleComplete">✔</button>
    <button @click="deleteTodo">✖</button>
  </li>
</template>

<script>
export default {
  props: ['todo'],
  methods: {
    toggleComplete() {
      this.$emit('toggle-complete', this.todo.id);
    },
    deleteTodo() {
      this.$emit('delete-todo', this.todo.id);
    }
  }
}
</script>

<style scoped>
li {
  list-style: none;
  margin: 5px 0;
  padding: 5px;
  background-color: #f4f4f4;
  border: 1px solid #ddd;
}
.completed {
  text-decoration: line-through;
  color: #888;
}
</style>
