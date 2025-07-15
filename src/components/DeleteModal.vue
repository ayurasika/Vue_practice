<template>
    <div class="modal">
      <p>本当に削除してもよろしいですか？😱</p>
      <button @click="handleDelete">削除する</button>
      <button @click="$emit('close')">キャンセル</button>
    </div>
  </template>
  
  <script setup>
  const emit = defineEmits(['close'])
  
  function handleDelete() {
    alert('削除しました！（実際はまだしてないわよ💥）')
    emit('close') // 親に「モーダル閉じて！」と伝える
  }
  </script>
  
  <style scoped>
  .modal {
    background: #fff;
    border: 2px solid #aaa;
    padding: 1rem;
    max-width: 300px;
    margin: 2rem auto;
    box-shadow: 0 0 10px #999;
  }
  </style>