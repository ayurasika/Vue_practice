<template>
    <form @submit.prevent="onSubmit">
      <input v-model="localUser.name" placeholder="名前（B）" />
      <input v-model="localUser.age" placeholder="年齢（B）" />
      <button type="submit">送信</button>
    </form>
  </template>
  
  <script setup>
  import { ref, watch } from 'vue'
  const props = defineProps(['user'])
  const emit = defineEmits(['submit'])
  
  const localUser = ref({ ...props.user })
  
  watch(() => props.user, (newVal) => {
    localUser.value = { ...newVal }
  })
  
  function onSubmit() {
    emit('submit', localUser.value)
  }
  </script>