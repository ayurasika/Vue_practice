<template>
  <div class="app">
    <h1>今日のTodoリストよ！♡</h1>
    <todo-item
      v-for="todo in todos"
      :key="todo.id"
      :task="todo.text"
      :is-completed="todo.completed"
      @toggle-complete="handleToggleComplete(todo.id)"
    />
    <p v-if="allCompleted">全部おわり！</p>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import TodoItem from './components/TodoItem.vue'

const todos = ref([
  { id: 1, text: '買い物に行く', completed: false },
  { id: 2, text: 'ちりつもラジオ', completed: true },
  { id: 3, text: 'ネイル', completed: false }
])

const allCompleted = computed(() => {
  return todos.value.every(todo => todo.completed)
})

function handleToggleComplete(todoId) {
  const todo = todos.value.find(t => t.id === todoId)
  if (todo) {
    todo.completed = !todo.completed
    console.log(`タスク「${todo.text}」の完了状態が変更されたわ！`)
  }
}
</script>

<style scoped>
.app {
  background-color: #ffffff;
  min-height: 100vh; /* 画面全体の高さに合わせる */
  color: #333;
  text-align: center;
  margin-bottom: 10px;
}
</style>