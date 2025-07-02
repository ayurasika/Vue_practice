<template>
<div>
<button
v-for="(btn, index) in buttons":key="index"
@click="handleClick(btn)"
@mouseover="hoverIndex = index"
@mouseleave="hoverIndex = null"
:class="{ hovered: hoverIndex === index }">
{{ btn }}
    </button>
</div>
</template>

<script setup>
import { ref } from 'vue';

const buttons = ["ボタンA", "ボタンB", "ボタンC"];
const hoverIndex = ref(null);

function handleClick(label) {
  alert(`${label} がクリックされたわよ〜！`);
}
</script>
<style>
button.hovered {
  background-color: coral;
  color: white;
}
</style>