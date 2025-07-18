<template>
  <div>
    <h1>ユーザー選択</h1>
    <select v-model="selectedId">
      <option value="1">ユーザー1</option>
      <option value="2">ユーザー2</option>
      <option value="3">ユーザー3</option>
    </select>

    <UserProfile :user-id="selectedId" />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import UserProfile from './UserProfile.vue';

const selectedId = ref(1);
</script>