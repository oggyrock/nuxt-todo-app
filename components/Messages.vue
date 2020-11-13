<template>
  <div class="messages">
    <transition-group name="opacity">
      <div
        v-for="message in messages"
        :key="message.id"
        :class="{ message, failure: !message.success }"
      >
        {{ message.title }}
      </div>
    </transition-group>
  </div>
</template>

<script>
export default {
  props: {
    messages: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>
.messages {
  position: absolute;
  left: 102%;
  top: 0;
}

.message {
  color: black;
  top: -2px;
  left: 85px;
  font-size: 16px;
  padding: 10px;
  margin-bottom: 10px;
  background-color: lightgreen;
  border: 1px solid grey;
  border-radius: 3px;
}

.failure {
  background-color: lightsalmon;
}

@media (max-width: 768px) {
  .message {
    font-size: 12px;
  }
}

@media (max-width: 500px) {
  .messages {
    left: 80%;
    right: 0;
    top: 50px;
  }
}

.opacity-enter-active,
.opacity-leave-active {
  transition: opacity 1s;
}

.opacity-enter,
.opacity-leave-to {
  opacity: 0;
}

.opacity-move {
  transition: all .3s
}
</style>
