<template>
  <div class="app">
    <h1>今日のTodoリストよ！♡</h1>
    <todo-item
      v-for="todo in todos"
      :key="todo.id"
      :id="todo.id"
      :task="todo.text"
      v-model:isCompleted="todo.completed"
      @delete-todo="deleteTodo"
    />
    <p v-if="allCompleted">全部おわり！</p>
  </div>


   <AddTaskForm 
   @pushTask="addTask"
  />

  <p class="remaining-count" v-if="remainingCount > 0">
    残り{{ remainingCount }}個です！がんばれ！</p>

</template>
<script setup>
import { ref, computed, watch  } from 'vue'
import TodoItem from './components/TodoItem.vue'
import AddTaskForm from './components/AddTaskForm.vue' 
const todos = ref([
  { id: 1, text: 'だいふくと遊ぶ', completed: false },
  { id: 2, text: 'Vue学習', completed: true },
  { id: 3, text: 'ピアノの練習', completed: false }
])

const allCompleted = computed(() => {
  return todos.value.every(todo => todo.completed)
})

function addTask(taskText) {
  // if (newTask.value.trim() === '') return

  const maxId = Math.max(...todos.value.map(todo => todo.id), 0)
  const newId = maxId + 1

  todos.value.push({
    id: newId,
    text: taskText,
    completed: false
  })

  // newTask.value = ''
}

function deleteTodo(id) {
  todos.value = todos.value.filter(todo => todo.id !== id)
}

watch(todos, (newTask) => {
  const ids = newTask.map(todo => todo.id)
  const hasDuplicates = ids.some((id, index) => ids.indexOf(id) !== index)

  console.log('🧾 現在のID一覧:', ids)

  if (hasDuplicates) {
    console.warn('⚠️ IDが重複してるわよぉ〜！！')
  }
}, { deep: true })

const remainingCount = computed(() => {
  return todos.value.filter(todo => !todo.completed).length
})
</script>
<style scoped>
body {
  background-color: #fff;
}
.app {
  background-color: #ffffff;
  min-height: 100vh;
  color: #333;
  text-align: center;
  margin-bottom: 10px;
}

.form input[type="text"] {
  padding: 0.4em 0.8em;
  font-size: 0.9rem;
  border: 1px solid #ccc;
  border-radius: 6px;
  outline: none;
  width: 200px;
  box-sizing: border-box;
  transition: border-color 0.2s ease;
}

input[type="text"]:focus {
  border-color: #ff66b2; /* 可愛いピンクに♡ */
}

button {
  padding: 0.5em 1em;
  font-size: 1rem;
  background-color: #ff66b2;
  color: white;
  border: none;
  border-radius: 8px;
  margin-left: 0.5em;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #ff3385;
}

.remaining-count {
  color: #ff66b2;
  font-size: 0.9rem;
  margin-top: 0.5em;
}
</style>
