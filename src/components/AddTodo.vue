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
