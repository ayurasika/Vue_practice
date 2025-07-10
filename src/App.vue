<template>
  <div class="tab-wrapper">
    <div class="tab-buttons">
      <button
        :class="{ active: currentTab === 'PageA' }"
        @click="currentTab = 'PageA'"
      >
        タブA
      </button>
      <button
        :class="{ active: currentTab === 'PageB' }"
        @click="currentTab = 'PageB'"
      >
        タブB
      </button>
    </div>

    <div class="tab-content">
      <keep-alive>
        <component :is="components[currentTab]" />
      </keep-alive>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import PageA from './components/PageA.vue'
import PageB from './components/PageB.vue'

const currentTab = ref('PageA')

const components = {
  PageA,
  PageB
}
</script>

<style scoped>
.tab-wrapper {
  max-width: 600px;
  margin: 2rem auto;
  font-family: sans-serif;
}

.tab-buttons {
  display: flex;
  gap: 10px;
  margin-bottom: 1rem;
}

.tab-buttons button {
  flex: 1;
  padding: 10px 20px;
  background: #eee;
  border: none;
  cursor: pointer;
  font-weight: bold;
  border-radius: 5px 5px 0 0;
  transition: background 0.3s;
}

.tab-buttons button.active {
  background: #4caf50;
  color: white;
}

.tab-content {
  padding: 1rem;
  border: 2px solid #4caf50;
  border-radius: 0 5px 5px 5px;
  background: #fafafa;
}
</style>