<template>
  <div class="buttonLayout">
    <NumberButton :value="1" :onClick="handleNumberClick" />
    <NumberButton :value="2" :onClick="handleNumberClick" />
    <NumberButton :value="3" :onClick="handleNumberClick" />
    <br>
    <NumberButton :value="4" :onClick="handleNumberClick" />
    <NumberButton :value="5" :onClick="handleNumberClick" />
    <NumberButton :value="6" :onClick="handleNumberClick" />
    <br>
    <NumberButton :value="7" :onClick="handleNumberClick" />
    <NumberButton :value="8" :onClick="handleNumberClick" />
    <NumberButton :value="9" :onClick="handleNumberClick" />
    <br>
    <ButtonDummy />
    <NumberButton :value="0" :onClick="handleNumberClick" />
    <ButtonDummy />
  </div>
</template>

<script setup>
import NumberButton from '../components/atoms/NumberButton.vue';
import FunctionButton from '../components/atoms/FunctionButton.vue';
import ButtonDummy from '../components/atoms/ButtonDummys.vue';

function handleNumberClick(number) {
    console.log('Button clicked:', number);
}
</script>

<style scoped>
.buttonLayout {
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    max-width: 300px;
    margin: 0 auto;
    background: blue;
    padding: 10px;
    gap: 10px;
}

</style>
