<template>
  <h1 class="index">Child2</h1>
  <div>{{ msg }}</div>
  <input type="text" v-model="inputValue" />
  <button @click="handleClickMsg">更新msg</button>
  <div>{{ provideKey }}</div>
</template>

<script setup lang="ts">
import { ref, inject } from 'vue';
defineProps({
  msg: {
    type: String,
  },
});

const emit = defineEmits(['handleChangeMsg']);

const handleClickMsg = () => {
  emit('handleChangeMsg', inputValue.value);
};

const inputValue = ref('hhhhhh');
defineExpose({ inputValue });

const provideKey = inject('provideKey');
</script>

<style lang="less" scoped></style>
