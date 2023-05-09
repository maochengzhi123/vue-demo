<script setup>
import { useStore } from '@/stores/counter';
const store = useStore();
</script>
<template>
  <div class="count">{{ store.count }}</div>
</template>

<style></style>
