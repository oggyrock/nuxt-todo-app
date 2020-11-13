<template>
  <ul class="todo-list">
    <li
      v-for="todo in todos"
      :key="todo.id"
      class="todo"
      @dblclick="removeTodo(todo.id)"
    >
      {{ todo.title }}
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    todos: {
      type: Array,
      required: true
    },
    removeTodo: {
      type: Function,
      required: true
    }
  }
}
</script>

<style scoped>
.todo-list {
  display: flex;
  flex-direction: column;
  padding: 0;
  margin: 0;
}

.todo {
  list-style: none;
  padding: 10px;
  margin-top: 10px;
  border: 1px solid gray;
  border-radius: 3px;
  background-color: white;
  transition: all 1s;
}

.todo:hover {
  background-color: wheat;
}
</style>
