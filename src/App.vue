<!-- 親コンポーネント -->
<template>
  <button @click="show = !show">切り替え</button>
  <TimerComponent v-if="show" />
</template>

<script setup>
import { ref } from 'vue'
import TimerComponent from './components/TimerComponent.vue'

const show = ref(false)
</script>
