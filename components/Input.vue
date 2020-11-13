<template>
  <input
    :value="title"
    class="input"
    type="text"
    placeholder="Введіть справу"
    @input="addTitle()"
  >
</template>

<script>
export default {
  props: {
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
.input {
  font-size: inherit;
  padding: 10px;
  border-radius: 3px;
  border: 1px solid gray;
  transition: all 1s;
}

.input:hover,
.input:focus {
  background-color: wheat;
}
</style>
