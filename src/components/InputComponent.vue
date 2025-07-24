<template>
    <input 
      :value="modelValue" 
      @input="onInput" 
      placeholder="お名前を入力してください"
    >
  </template>
  
  <script setup>
  // v-modelのルールに従い、props名を'modelValue'にする
  defineProps({
    modelValue: String
  });
  
  // v-modelのルールに従い、emit名を'update:modelValue'にする
  const emit = defineEmits(['update:modelValue']);
  
  function onInput(event) {
    // 'update:modelValue'イベントを親へ発行する
    emit('update:modelValue', event.target.value);
  }
  </script>
  
  <style scoped>
  /* このコンポーネントのみに適用されるスタイル */
  input {
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 4px;
    font-size: 16px;
    width: 250px;
  }
  </style>