<template>
  <keep-alive>
    <MyPage v-if="showPage" />
  </keep-alive>

  <button @click="showPage = !showPage">切り替えボタン</button>
</template>

<script setup>
import { ref } from 'vue'
import MyPage from './components/MyPage.vue'

const showPage = ref(true)
</script>