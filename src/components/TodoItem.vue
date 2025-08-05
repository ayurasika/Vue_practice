<template>
  <div class="todo-item">
    <input type="checkbox" v-model="isCompleted" />
    <span :class="{ done: isCompleted }">{{ task }}</span>
    <button @click="deleteTodo">削除</button>
  </div>
</template>

<script setup>
const props = defineProps(['task', 'id'])
const isCompleted = defineModel('isCompleted')

const emit = defineEmits(['delete-todo'])

function deleteTodo() {
  emit('delete-todo', props.id)
}
</script>

<style scoped>
.todo-item {
  display: flex;
  align-items: center;
  gap: 0.5em;
  margin: 0.5em 0;
}
.done {
  text-decoration: line-through;
  color: gray;
}
</style>