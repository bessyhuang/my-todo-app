<template>
  <div id="app">
    <h1>To-Do List</h1>
    <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Add a new todo" />
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        <input type="checkbox" v-model="todo.completed" />
        <span :class="{ completed: todo.completed }">{{ todo.text }}</span>
        <button @click="removeTodo(index)">Remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      newTodo: '',
      todos: [
        { text: 'Learn Vue.js', completed: false },
        { text: 'Build a To-Do App', completed: false }
      ]
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() === '') return;
      this.todos.push({
        text: this.newTodo,
        completed: false
      });
      this.newTodo = '';
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    }
  }
};
</script>

<style>
.completed {
  text-decoration: line-through;
}
input[type="checkbox"] {
  margin-right: 10px;
}
button {
  margin-left: 10px;
  color: red;
  background: none;
  border: none;
  cursor: pointer;
}
</style>

