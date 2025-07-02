<template>
    <div :class="{ 'completed-task': isCompleted }">
      <input type="checkbox" :checked="isCompleted" @change="toggleItem" />
      <span>{{ task }}</span>
    </div>
  </template>
  
  <script setup>
  import { defineProps, defineEmits } from 'vue';
  
  const props = defineProps({
    task: {
      type: String,
      required: true
    },
    isCompleted: {
      type: Boolean,
      required: true
    }
  });
  
  const emit = defineEmits(['toggle-complete']);
  
  function toggleItem() {
    emit('toggle-complete');
    console.log(`子で「${props.task}」の完了状態変更を親に伝えたわ！`);
  }
  </script>
  
  <style scoped>
  .completed-task {
    text-decoration: line-through;
    color: #aaa;
  }
  </style>