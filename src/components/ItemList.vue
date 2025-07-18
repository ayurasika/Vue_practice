<template>
    <ul>
      <li v-for="(item, index) in items" :key="index">
        <slot :item="item" :index="index">
          <!-- fallback：デフォルト表示 -->
          {{ item }}
        </slot>
      </li>
    </ul>
  </template>
  
  <script setup>
  defineProps({
    items: {
      type: Array,
      required: true
    }
  });
  </script>