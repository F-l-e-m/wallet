<template>
  <button @click="$emit('click')">
    {{ text }}
  </button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    text: {
      type: String,
      default: '',
    },
  },
}
</script>

<style scoped>
button {
  cursor: pointer;
  border: none;
  font-weight: bold;
  font-size: 14px;
  line-height: 16px;
  color: #fff;
  padding: 12px 54px;
  border-radius: 3px;
  background: linear-gradient(88.29deg, #2f80ed 1.44%, #de16ca 100%);
}

input::placeholder {
  color: #fff;
}
</style>
