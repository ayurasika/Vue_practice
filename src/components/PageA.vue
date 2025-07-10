<template>
    <div>
      <h2>🌸 これは Page A よ！</h2>
      <p>カウント: {{ count }}</p>
      <button @click="count++">+1</button>
    </div>
  </template>
  
  <script setup>
  import { ref, onActivated, onDeactivated } from 'vue'
  
  const count = ref(0)
  
  onActivated(() => {
    console.log('✨ Page A が表示されたわ！')
  })
  onDeactivated(() => {
    console.log('🧹 Page A は裏に隠れたわ〜')
  })
  </script>