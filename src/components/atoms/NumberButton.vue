<template>
  <button @click="onClick(props.value)">{{ props.value }}</button>
</template>

<script setup>
const props = defineProps({
  value: {
    type: Number,
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
  background-color: green;
  border: 1px solid green;
}
</style>
