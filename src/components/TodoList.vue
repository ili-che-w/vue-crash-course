<template>
  <div>
    <ul>
      <TodoItem v-for="(todo, idx) in todos" :key="idx" :todo="todo" />
    </ul>
  </div>
</template>

<script>
import TodoItem from '@/components/TodoItem'
export default {
  props: ['todos'],
  components: {
    TodoItem
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
