<script setup>
import { useStore } from '@/stores/counter';
const store = useStore();
</script>

<template>
  <div class="count">{{ store.count }}</div>
  <div class="buttons">
    <button @click="store.decreaseCount">-</button>
    <button @click="store.increaseCount">+</button>
  </div>
</template>

<style>
.count {
  font-size: 60px;
  text-align: center;
}
.buttons {
  text-align: center;
}
button {
  margin: 10px;
  font-size: 40px;
}
</style>
