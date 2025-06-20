<template>
  <button @click="onClick">{{ props.label }}</button>
</template>

<script setup>
const props = defineProps({
  label: {
    type: String,
    required: true
  },
  onClick: {
    type: Function,
    required: true
  }
});
</script>

<style scoped>
button {
  flex: 1 0 30%;
  font-size: 20px;
  padding: 15px;
  background-color: blue;
  border: 1px solid blue;
}
</style>
