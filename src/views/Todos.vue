<template>
  <div class="container">
    <h2>Todo list</h2>
    <AddTodo @add-todo-item="addTodoItem" />
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
