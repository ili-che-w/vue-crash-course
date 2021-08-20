<template>
  <li class="todo">
    <input
      type="checkbox"
      class="todo__checkbox"
      :id="`todo_${index}`"
      @change="todo.completed = !todo.completed"
    />

    <label
      :for="'todo_' + index"
      class="todo__title"
      :class="{ 'todo__title--completed': todo.completed }"
    >
      <strong>{{ index }}</strong>
      {{ todo.title | uppercase }}
    </label>

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
    },
    index: {
      type: Number,
      required: true
    }
  },
  filters: {
    uppercase(value) {
      return value.toUpperCase()
    }
  }
}
</script>

<style scoped>
.todo {
  display: flex;
  align-items: center;
  margin-bottom: 1rem;
  padding: 0.5rem 2rem;
  border: 1px solid #ccc;
}

.todo__remove {
  height: 25px;
  width: 25px;
  margin-left: auto;
  border: none;
  border-radius: 50%;
  font-size: 20px;
  line-height: 25px;
  background-color: rgb(206, 23, 23);
  color: white;
}

.todo__checkbox,
.todo__title,
.todo__remove {
  cursor: pointer;
}

.todo__checkbox {
  margin-right: 1rem;
}

.todo__title {
  text-align: left;
  padding-right: 2rem;
}

.todo__title--completed {
  color: #aaa;
  text-decoration: line-through;
}
</style>
