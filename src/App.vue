<template>
  <div id="app">
    <h1>Todo list</h1>
    <AddTodo 
      @add-todo="addTodo"
    />
    <select v-model="filter">
      <option value="all">All</option>
      <option value="completed">Completed</option>
      <option value="not-completed">Not-completed</option>
    </select>
    <TodoList
      :todos="filterdTodos"
      @remove-todo="removeTodo"
      />
  </div>
</template>

<script>
import TodoList from '@/components/TodoList'
import AddTodo from '@/components/AddTodo'

export default {
  name: 'App',
  components: {
    TodoList,
    AddTodo,
  },
  data() {
    return {
      todos: [
        {id: 1, title: 'Todo item 1', completed: false},
        {id: 2, title: 'Todo item 2', completed: false},
        {id: 3, title: 'Todo item 3', completed: false},
      ],
      filter: 'all',
    }
  },
  computed: {
    filterdTodos() {
      let filter;

      if (this.filter === 'all') {
        return this.todos
      }

      if (this.filter === 'completed') {
        return this.todos.filter(t => t.completed)
      }

      if (this.filter === 'not-completed') {
        return this.todos.filter(t => !t.completed)
      }

      return filter;
    }
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      this.todos.push(newTodo)
    }

  }
}
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
</style>
