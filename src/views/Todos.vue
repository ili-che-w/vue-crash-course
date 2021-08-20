<template>
  <div class="container">
    <h2>Todo list</h2>

    <div class="row">
      <AddTodo @add-todo-item="addTodoItem" />

      <select v-model="filter">
        <option value="all">All</option>
        <option value="completed">Completed</option>
        <option value="uncompleted">Uncompleted</option>
      </select>
    </div>

    <Loader v-if="loading" />

    <TodoList
      :todos="todosFiltered"
      @remove-todo-item="removeTodoItem"
      v-else-if="todos.length"
    />

    <p v-else>
      <em>No todos</em>
    </p>
  </div>
</template>

<script>
import TodoList from '@/components/TodoList'
import AddTodo from '@/components/AddTodo'
import Loader from '@/components/Loader'

export default {
  name: 'App',
  data() {
    return {
      todos: [],
      loading: true,
      filter: 'all'
    }
  },
  computed: {
    todosFiltered() {
      switch (this.filter) {
        case 'all':
          return this.todos
        case 'completed':
          return this.todos.filter(todo => todo.completed)
        case 'uncompleted':
          return this.todos.filter(todo => !todo.completed)
        default:
          return []
      }
    }
  },
  components: {
    TodoList,
    AddTodo,
    Loader
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(response => response.json())
      .then(json => {
        setTimeout(() => {
          this.todos = json
          this.loading = false
        }, 1000)
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
