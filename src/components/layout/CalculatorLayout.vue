<template>
  <div class="calculator">
    <div class="display">{{ display }}</div>

    <div class="buttons">
      <NumberButton v-for="n in [1,2,3,4,5,6,7,8,9,0]" :key="n" :value="n" :onClick="appendNumber" />

      <FunctionButton label="+" :onClick="() => chooseOperator('+')" />
      <FunctionButton label="-" :onClick="() => chooseOperator('-')" />
      <FunctionButton label="*" :onClick="() => chooseOperator('*')" />
      <FunctionButton label="/" :onClick="() => chooseOperator('/')" />
      <FunctionButton label="C" :onClick="clear" />
      <FunctionButton label="=" :onClick="calculate" />
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import NumberButton from '../atoms/NumberButton.vue';
import FunctionButton from '../atoms/FunctionButton.vue';

const current = ref('');
const previous = ref('');
const operator = ref(null);

const display = computed(() => current.value || '0');

function appendNumber(num) {
  current.value += num.toString();
}

function chooseOperator(op) {
  if (current.value === '') return;
  if (previous.value !== '') calculate();
  operator.value = op;
  previous.value = current.value;
  current.value = '';
}

function calculate() {
  let result;
  const number1 = parseFloat(previous.value);
  const number2 = parseFloat(current.value);

  if (isNaN(number1) || isNaN(number2)) return;

  switch (operator.value) {
    case '+': result = number1 + number2; break;
    case '-': result = number1 - number2; break;
    case '*': result = number1 * number2; break;
    case '/': result = number2 !== 0 ? number1 / number2 : 'Error'; break;
    default: return;
  }

  current.value = result.toString();
  operator.value = null;
  previous.value = '';
}

function clear() {
  current.value = '';
  previous.value = '';
  operator.value = null;
}
</script>

<style scoped>
.calculator {
  width: 320px;
  margin: 20px auto;
  padding: 20px;
  background: #e3e3e3;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.display {
  background: black;
  color: white;
  padding: 20px;
  font-size: 2rem;
  text-align: right;
}

.buttons {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}
</style>
