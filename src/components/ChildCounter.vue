<template>
    <div>
      <button @click="increment">カウント +1</button>
    </div>
  </template>
  
  <script setup>
  import { ref, watch } from 'vue'
  
  // 親からの初期値を受け取る
  const props = defineProps({
    startCount: {
      type: Number,
      required: true
    }
  })
  
  // emitの準備
  const emit = defineEmits(['update'])
  
  const count = ref(props.startCount)
  
  // ボタンがクリックされたとき
  function increment() {
    count.value++
    emit('update', count.value) // 親へ「新しいカウントよ〜！」と通知
  }
  </script>