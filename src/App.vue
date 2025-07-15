<template>
  <div>
    <button @click="current = 'A'">フォームA</button>
    <button @click="current = 'B'">フォームB</button>

    <FormA v-if="current === 'A'" :user="user" @submit="handleSubmit" />
    <FormB v-else :user="user" @submit="handleSubmit" />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import FormA from './components/FormA.vue'
import FormB from './components/FormB.vue'

const current = ref('A')
const user = ref({ name: '', age: '' })

function handleSubmit(data) {
  console.log('送信されたデータよ〜✨', data)
}
</script>