<template>
    <div v-if="userData">
      <h2>{{ userData.name }} さん</h2>
      <img :src="userData.avatar" alt="プロフィール画像" width="100" />
      <p>{{ userData.age }}歳</p>
      <p>{{ userData.bio }}</p>
    </div>
    <div v-else>
      読み込み中…
    </div>
  </template>
  
  <script setup>
  import { ref, watch } from 'vue';
  import { useRoute } from 'vue-router';
  
  const props = defineProps({
    userId: Number
  });
  
  const userData = ref(null);
  
  watch(() => props.userId, async (id) => {
    userData.value = null; // 読み込み中表示用
    try {
      const res = await fetch(`https://example.com/api/user/${id}`);
      if (!res.ok) throw new Error('エラーが発生したわ！');
      const data = await res.json();
      userData.value = data;
    } catch (e) {
      console.error('取得失敗:', e);
    }
  }, { immediate: true }); // 初回にも即 fetch するため
  </script>