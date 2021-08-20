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
  display: flex;
  justify-content: space-between;
  margin-bottom: 1rem;
  padding: 0.5rem 2rem;
  border: 1px solid #ccc;
}

.todo__remove {
  height: 25px;
  width: 25px;
  border: none;
  border-radius: 50%;
  font-size: 20px;
  line-height: 25px;
  background-color: rgb(206, 23, 23);
  color: white;
  cursor: pointer;
}

.todo__checkbox {
  margin-right: 1rem;
}

.todo--completed {
  text-decoration: line-through;
}
</style>
