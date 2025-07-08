<!-- TimerComponent.vue -->
<template>
    <div>タイマーコンポーネント</div>
</template>

<script setup>
import { onMounted, onBeforeUnmount, ref } from 'vue'

const intervalId = ref()

onMounted(() => {
    intervalId.value = setInterval(() => {
console.log('🕒 動いてるわよ〜')
    }, 1000)
})

onBeforeUnmount(() => {
    clearInterval(intervalId.value)
    console.log('🧹 お片付けよ！（onBeforeUnmount）')
})
</script>
