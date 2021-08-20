<template>
  <form @submit.prevent="createTodoItem">
    <input type="text" v-model="title" />
    <button type="submit">Create</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: ''
    }
  },
  methods: {
    createTodoItem() {
      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          completed: false
        }

        this.$emit('add-todo-item', newTodo)
        this.title = ''
      }
    }
  }
}
</script>

<style scoped>
form {
  display: flex;
  margin-bottom: 2rem;
}

input {
  min-width: 300px;
  border: 1px solid #ccc;
  border-radius: 0;
  padding: 0.5rem;
  font-size: 16px;
  color: #2c3e50;
}

input:active,
input:focus {
  outline: none;
}

button {
  border: 1px solid #ccc;
  border-radius: 0;
  border-left: none;
  padding: 0.5rem 2rem;
  font-family: sans-serif;
  font-size: 16px;
  color: #2c3e50;
}
</style>
