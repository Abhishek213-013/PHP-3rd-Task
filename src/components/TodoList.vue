<template>
    <div>
      <input v-model="newTodo" placeholder="Add a new task" @keyup.enter="addTodo" />
      <ul>
        <TodoItem 
          v-for="todo in todos" 
          :key="todo.id" 
          :todo="todo" 
          @toggle-complete="toggleComplete" 
          @delete-todo="deleteTodo"
        />
      </ul>
    </div>
  </template>
  
  <script>
  import TodoItem from './TodoItem.vue';
  
  export default {
    components: { TodoItem },
    data() {
      return {
        newTodo: '',
        todos: [
          { id: 1, text: 'Learn Vue.js', completed: false },
          { id: 2, text: 'Build a todo app', completed: false }
        ]
      };
    },
    methods: {
      addTodo() {
        if (this.newTodo) {
          this.todos.push({
            id: this.todos.length + 1,
            text: this.newTodo,
            completed: false
          });
          this.newTodo = '';
        }
      },
      toggleComplete(id) {
        const todo = this.todos.find(todo => todo.id === id);
        todo.completed = !todo.completed;
      },
      deleteTodo(id) {
        this.todos = this.todos.filter(todo => todo.id !== id);
      }
    }
  }
  </script>
  
  <style scoped>
  input {
    width: 100%;
    padding: 10px;
    margin-bottom: 10px;
    border: 1px solid #ddd;
  }
  ul {
    padding: 0;
  }
  </style>
  