<template>
    <button @click="handleClick">カウントアップ</button>
</template>

<script setup>
import { ref } from 'vue'

defineProps({
    startCount:Number,
})  

function handleClick() {
    startCount.value++
    emit('clicked')
}
</script>



const emit = defineEmits(['clicked'])