<template>
  <form
    class="add-todo-form"
    @submit.prevent="addTodo"
  >
    <Input
      :title="title"
      :add-title="addTitle"
    />
    <Button :title="title" />
    <Messages :messages="messages" />
  </form>
</template>

<script>
export default {
  props: {
    messages: {
      type: Array,
      required: true
    },
    addTodo: {
      type: Function,
      required: true
    },
    title: {
      type: String,
      required: true
    },
    addTitle: {
      type: Function,
      required: true
    }
  }
}
</script>

<style scoped>
.form {
  display: flex;
  flex-direction: row;
}
</style>
