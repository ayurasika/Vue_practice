<template>
  <div :style="{ backgroundColor: myColor }" class="color-box"> <h2>背景色が変わる魔法の箱</h2>
    <button @click="changeColor">色を変える魔法のボタン</button> </div>
</template>

<script setup>
import { ref } from 'vue'; // 大事な魔法の道具を呼んでるわ

const myColor = ref('lightblue'); // ①これが、色をしまっておく箱よ。最初は水色ね。

// ②これが、色を変える魔法の呪文よ
function changeColor() {
  if (myColor.value === 'lightblue') {
    myColor.value = 'lightcoral'; // もし今の色が水色なら、サンゴ色に変えるわ
  } else {
    myColor.value = 'lightblue'; // それ以外なら、水色に戻すわ
  }
}
</script>

<style scoped>
.color-box {
  width: 300px;
  height: 200px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  border: 2px solid #333;
  transition: background-color 0.5s ease; /* 色が変わるときにゆっくり変化する魔法よ */
}
</style>