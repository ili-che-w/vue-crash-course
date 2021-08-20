<template>
  <div id="app">
    <h1>Todo application</h1>
    <AddTodo @add-todo-item="addTodoItem" />
    <hr />
    <TodoList :todos="todos" @remove-todo-item="removeTodoItem" />
  </div>
</template>

<script>
import TodoList from '@/components/TodoList'
import AddTodo from '@/components/AddTodo'

export default {
  name: 'App',
  data() {
    return {
      todos: []
    }
  },
  components: {
    TodoList,
    AddTodo
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(response => response.json())
      .then(json => {
        this.todos = json
      })
  },
  methods: {
    removeTodoItem(id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
    },
    addTodoItem(todo) {
      this.todos.push(todo)
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
