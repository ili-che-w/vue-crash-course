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
