<template>
  <div :class="bgClass" class="box">
    <p>{{ message }}</p>
    <button @click="toggleLogin">{{ buttonLabel }}</button>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const isLoggedIn = ref(false)

// 背景クラスを computed で切り替える！
const bgClass = computed(() =>
  isLoggedIn.value ? 'bg-logged-in' : 'bg-logged-out'
)

const message = computed(() =>
  isLoggedIn.value ? 'ようこそ、あゆみちゃんさん✨' : 'ログインしてください'
)

const buttonLabel = computed(() =>
  isLoggedIn.value ? 'ログアウトする' : 'ログインする'
)

const toggleLogin = () => {
  isLoggedIn.value = !isLoggedIn.value
}
</script>

<style scoped>
.box {
  padding: 2rem;
  text-align: center;
  border-radius: 12px;
  transition: all 0.3s ease;
}

/* ログイン状態の背景色 */
.bg-logged-in {
  background-color: #d0f0c0; /* 薄い緑 */
}

/* ログアウト状態の背景色 */
.bg-logged-out {
  background-color: #ffe4e1; /* 薄いピンク */
}
</style>
