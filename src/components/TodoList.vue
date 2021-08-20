<template>
  <div>
    <ul>
      <TodoItem
        v-for="(todo, idx) in todos"
        :key="idx"
        :index="idx + 1"
        :todo="todo"
        @remove-todo-item="removeTodoItem"
      />
    </ul>
  </div>
</template>

<script>
import TodoItem from '@/components/TodoItem'
export default {
  props: ['todos'],
  components: {
    TodoItem
  },
  methods: {
    removeTodoItem(id) {
      this.$emit('remove-todo-item', id)
    }
  }
}
</script>

<style scoped>
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}
</style>
