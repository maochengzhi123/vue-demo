<template>
  <h1 class="index">Child1-Child</h1>
  {{ provideKey }}
</template>

<script setup lang="ts">
import { inject } from 'vue';
const provideKey = inject('provideKey');
</script>

<style lang="less" scoped></style>
