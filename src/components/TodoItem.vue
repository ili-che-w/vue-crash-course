<template>
  <li>
    <span :class="{ 'todo--completed': todo.completed }">
      <input
        type="checkbox"
        class="todo__checkbox"
        @change="todo.completed = !todo.completed"
      />
      <strong>{{ todo.id }}</strong>
      {{ todo.title }}
    </span>

    <button class="todo__remove" @click="$emit('remove-todo-item', todo.id)">
      &times;
    </button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
li {
  border: 1px solid #ccc;
  display: flex;
  justify-content: space-between;
  padding: 0.5rem 2rem;
  margin-bottom: 1rem;
}

.todo__remove {
  background-color: rgb(206, 23, 23);
  color: white;
  border: none;
  border-radius: 50%;
  font-size: 20px;
  line-height: 25px;
  height: 25px;
  width: 25px;
}

.todo__checkbox {
  margin-right: 1rem;
}

.todo--completed {
  text-decoration: line-through;
}
</style>
