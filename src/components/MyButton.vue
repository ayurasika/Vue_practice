<!-- MyButton.vue -->
<template>
    <button class="btn">
      <slot></slot>
    </button>
  </template>
  
  <script setup>
  // ロジックなしでOKよ💋
  </script>
  
  <style scoped>
  .btn {
    background-color: #f06292;
    color: white;
    padding: 8px 16px;
    border-radius: 8px;
    border: none;
    font-size: 16px;
  }
  </style>
  