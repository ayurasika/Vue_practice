<!-- 子コンポーネント -->
<template>
    <input v-model="localTask" />
    <button @click="addTask">追加</button>
</template>

<script setup>
import { ref } from 'vue'

const localTask = ref('')
const emit = defineEmits(['pushTask'])

function addTask() {
    if (localTask.value.trim()) {
        emit('pushTask', localTask.value)
        localTask.value = ''
    }
}
</script>