<template>
    <p>カチカチ動作中... コンソール見てね！</p>
</template>

<script setup>
import { onMounted, onUnmounted, ref } from 'vue'

const intervalId = ref(null)

onMounted(() => {
    intervalId.value = setInterval(() => {
console.log('⏰ カチカチ...（onMounted中）')
    }, 5000)
})

onUnmounted(() => {
    clearInterval(intervalId.value)
    console.log('🛑 タイマー止めたわよ（onUnmounted）')
})
</script>
