<template>
  <button>{{ value }}</button>
</template>

<script setup>
const props = defineProps({
  function: {
    type: String,
    required: true
  },
  onClick: {
    type: Function,
    required: true
  }
});

const { value, onClick } = props;
</script>

<style scoped>
button {
  font-size: 16px;
  padding: 10px;
  margin: 5px;
  background-color: #f0f0f0;
  border: 1px solid #ddd;
  cursor: pointer;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #ccc;
}
</style>
