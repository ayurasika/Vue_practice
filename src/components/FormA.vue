<template>
    <form @submit.prevent="handleSubmit">
      <input v-model="localUser.name" placeholder="名前" />
      <input v-model="localUser.age" placeholder="年齢" />
      <button type="submit">保存</button>
    </form>
</template>

<script setup>
import { ref, watch } from 'vue'

const props = defineProps(['user'])
const emit = defineEmits(['submit']) // ← 親に知らせるイベント名よ

const localUser = ref({ ...props.user })

watch(() => props.user, (newVal) => {
  localUser.value = { ...newVal }
})

// ボタン押したときに emit 発動！
function handleSubmit() {
  emit('submit', localUser.value)
}
</script>

