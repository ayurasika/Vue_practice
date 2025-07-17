<template>
    <div class="card">
      <slot>
        <p style="color: gray;">🪄 ここには何も渡されてないから、アタシが代わりに登場よ！</p>
      </slot>
    </div>
  </template>
  
  <script setup>
  </script>
  
  <style scoped>
  .card {
    padding: 16px;
    border: 2px dashed #999;
    border-radius: 8px;
  }
  </style>