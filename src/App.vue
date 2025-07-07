<template>
  <div>
    <button @click="toggle">表示／非表示 切り替え</button>
    <TimerComponent v-if="show" />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import TimerComponent from './components/TimerComponent.vue'

const show = ref(true)

const toggle = () => {
  show.value = !show.value
}
</script>
