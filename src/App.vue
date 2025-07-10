<template>
  <div class="list-wrapper">
    <button @click="addItem">追加する</button>

    <transition-group name="fade" tag="ul" class="list">
      <li v-for="item in items" :key="item.id" class="list-item">
        {{ item.text }}
        <button @click="removeItem(item.id)">削除</button>
      </li>
    </transition-group>
  </div>
</template>

<script setup>
import { ref } from 'vue'

let idCounter = 1
const items = ref([
  { id: idCounter++, text: 'アイテム1' },
  { id: idCounter++, text: 'アイテム2' }
])

function addItem() {
  items.value.push({ id: idCounter++, text: `アイテム${idCounter - 1}` })
}

function removeItem(id) {
  items.value = items.value.filter(item => item.id !== id)
}
</script>

<style scoped>
.list-wrapper {
  max-width: 400px;
  margin: 2rem auto;
  font-family: sans-serif;
}

button {
  margin-bottom: 1rem;
  padding: 0.5rem 1rem;
  background: #4caf50;
  color: white;
  border: none;
  cursor: pointer;
  border-radius: 5px;
}

.list {
  padding: 0;
  list-style: none;
}

.list-item {
  background: #eee;
  margin-bottom: 0.5rem;
  padding: 0.75rem 1rem;
  border-radius: 5px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

/* 🎨 アニメーション */
.fade-enter-active,
.fade-leave-active {
  transition: all 0.4s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateY(10px);
}

.fade-enter-to,
.fade-leave-from {
  opacity: 1;
  transform: translateY(0);
}
</style>
