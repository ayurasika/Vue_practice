<template>
    <div class="item">
      <slot :data="data">⚠️ 表示がないわよ</slot>
    </div>
  </template>
  
  <script setup>
  defineProps({
    data: Object
  });
  </script>