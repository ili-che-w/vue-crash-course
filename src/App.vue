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
      todos: [
        { id: 1, title: 'Buy bread', completed: false },
        { id: 2, title: 'Buy butter', completed: false },
        { id: 3, title: 'Buy beer', completed: false }
      ]
    }
  },
  components: {
    TodoList,
    AddTodo
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
