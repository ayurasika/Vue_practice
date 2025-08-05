<template>
  <div :class="['completed-task', isCompleted ? 'isCompleted' : '']">
    <input type="checkbox" :checked="isCompleted" @change="toggleItem" />
    <span>{{ task }}</span>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue'

const props = defineProps({
  task: {
    type: String,
    required: true
  },
  isCompleted: {
    type: Boolean,
    required: true
  }
})

const emit = defineEmits(['toggle-complete'])

function toggleItem() {
  emit('toggle-complete')
  console.log(`子で「${props.task}」の完了状態を親に伝えたわよ！`)
}
</script>

<style scoped>
.completed-task {
  margin: 8px 0;
}
.isCompleted {
  text-decoration: line-through;
  color: gray;
}
</style>