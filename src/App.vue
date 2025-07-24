<template>
  <div>
    <h1>親子コンポーネントの連携 (v-model版)</h1>

    <InputComponent v-model="name" />

    <p>{{ name }}さん、こんにちは！</p>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import InputComponent from './components/InputComponent.vue';

// 状態管理の仕方は変わらない
const name = ref('宝塚');
</script>

<style scoped>
div {
  display: grid;
  gap: 16px; /* 要素間のスペース */
  font-family: sans-serif;
}

p {
  font-size: 18px;
  font-weight: bold;
}
</style>