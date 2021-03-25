<template>
  <input
    type="text"
    :placeholder="placeholder"
    :value="value"
    @input="handleInput($event.target.value)"
  />
</template>

<script>
export default {
  name: 'Input',
  props: {
    placeholder: {
      type: String,
      default: '',
    },
    value: {
      type: [String, Number],
      default: '',
    },
  },
  methods: {
    handleInput(value) {
      this.$emit('input', value)
    },
  },
}
</script>

<style scoped>
input {
  padding: 12px 14px;
  color: #fff;
  font-size: 14px;
  border: 1px solid #ffffff;
  box-sizing: border-box;
  border-radius: 3px;
  background: transparent;
}

input::placeholder {
  color: #fff;
}
</style>
