<template>
  <div class="container">
    <h2 class="title">
      Список справ
    </h2>
    <div class="list-container">
      <Form
        :messages="messages"
        :add-todo="addTodo"
        :title="title"
        :add-title="addTitle"
      />
      <Todos
        :todos="todos"
        :remove-todo="removeTodo"
      />
    </div>
  </div>
</template>

<script>
import Todos from '../components/Todos.vue'
export default {
  components: { Todos },
  data: () => ({
    todos: [
      { id: 1, title: 'qwe' },
      { id: 2, title: 'ryt' },
      { id: 3, title: 'rew' },
      { id: 4, title: 'turio' }
    ],
    messages: [],
    title: ''
  }),

  methods: {
    addTitle (title) {
      this.title = event.target.value
    },

    addTodo (todo) {
      if (this.todos.some(todo => todo.title === this.title.trim())) {
        this.messages.unshift(this.createMessage('Вже додано', false))
        this.hideMessage()
        return
      }
      if (this.title.length > 30) {
        this.messages.unshift(this.createMessage('Максимальна довжина - 30 символів', false))
        this.hideMessage()
        return
      }

      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.title
        }
        this.todos.push(newTodo)
      }
      this.title = ''
      this.messages.unshift(this.createMessage('Успішно додано', true))
      this.hideMessage()
    },

    removeTodo (todoId) {
      this.todos = this.todos.filter(todo => todo.id !== todoId)
      this.messages.unshift(this.createMessage('Успішно видалено', true))
      this.hideMessage()
    },

    createMessage (message, success) {
      return { id: Date.now(), title: message, success }
    },

    hideMessage () {
      if (this.messages.length) {
        setTimeout(() => {
          this.messages.pop()
        }, 5000)
      }
    }
  }
}
</script>

<style>
body {
  margin: 0;
  padding: 0;
}

.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  font-size: 30px;
  background-color:seashell;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 70px;
  color: #35495e;
  letter-spacing: 1px;
}

.list-container {
  position: relative;
}

@media (max-width: 768px) {
  .container {
    font-size: 20px;
  }

  .title {
    font-size: 50px;
  }
}
</style>
