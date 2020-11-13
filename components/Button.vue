<template>
  <button
    class="button"
    :disabled="!title.length"
  >
    Додати
  </button>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true
    }
  }
}
</script>

<style scoped>
.button {
  font-size: inherit;
  padding: 10px;
  background-color: white;
  border: 1px solid gray;
  border-radius: 3px;
  transition: all 1s;
}

.button:hover {
  background-color: wheat;
}
</style>
