<template>
  <div>
    <h1>今日のTodoリストよ！💖</h1>
    <todo-item
      v-for="todo in todos"
      :key="todo.id"
      :task="todo.text"
      :is-completed="todo.completed"
      @toggle-complete="handleToggleComplete(todo.id)"
    ></todo-item>
    <p v-if="allCompleted">全部終わったわ！素晴らしい！🎉</p>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import TodoItem from './components/TodoItem.vue';

const todos = ref([
  { id: 1, text: '豆腐を買いに行く', completed: false },
  { id: 2, text: 'お風呂掃除', completed: true },
  { id: 3, text: 'ネイルを塗り直す', completed: false }
]);

function handleToggleComplete(todoId) {
  const todo = todos.value.find(t => t.id === todoId);
  if (todo) {
    todo.completed = !todo.completed; // 完了状態を反転させるわ
    console.log(`タスク「${todo.text}」の完了状態が変更されたわ！`);
  }
}

const allCompleted = computed(() => {
  return todos.value.every(todo => todo.completed);
});
</script>