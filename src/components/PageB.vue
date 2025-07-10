<template>
    <div>
      <h2>🌼 こちらは Page B よ〜</h2>
      <input v-model="message" placeholder="ここに入力してみて♪" />
      <p>入力した内容：{{ message }}</p>
    </div>
  </template>
  
  <script setup>
  import { ref, onActivated, onDeactivated } from 'vue'
  
  const message = ref('')
  
  onActivated(() => {
    console.log('✨ Page B が表示されたわ！')
  })
  onDeactivated(() => {
    console.log('🧹 Page B は裏に隠れたわ〜')
  })
  </script>
  