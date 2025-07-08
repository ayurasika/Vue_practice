<template>
    <p>こんにちは</p>
</template>

<script setup>
import { onMounted, onActivated, onDeactivated } from 'vue'

onMounted(() => {
console.log('🎬 初めて表示されたわよ！')
})

onActivated(() => {
console.log('🌈 また表示されたわよ！')
})

onDeactivated(() => {
console.log('🚪 隠れたわよ〜、またね！')
})
</script>
