<template>
  <li>
    <span :class="{done: todo.completed}">
      <input type="checkbox" @change="todo.completed = !todo.completed" />
      <strong>{{ index + 1 }}.</strong>
      {{ todo.title }}
    </span>
    <button @click="$emit('remove-todo', todo.id  )">
      &times;
    </button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
    index: {
      type: Number,
      required: true,
    }
  }
}
</script>

<style scoped>
  li {
    border: 1px solid #ccc;
    display: flex;
    justify-content: space-between;
    padding: 10px;
    margin-bottom: 10px;
  }

  button {
    background: red;
    color: #fff;
    font-weight: bold;
    border: none;
  }

  input {
    margin-right: 14px;
  }

  .done {
    text-decoration: line-through;
  }
</style>