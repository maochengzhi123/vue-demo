<template>
  <div>
    <h1 class="index">Child1</h1>
    <div>{{ msg }}</div>
    <Child />
  </div>
</template>

<script setup lang="ts">
import { getCurrentInstance, onMounted } from 'vue';
import Child from './Child1-Child.vue';
defineOptions({
  name: 'child1',
});
defineProps({
  msg: {
    type: String,
  },
});

const handleAlert = () => {
  alert('hello world');
};

const childMsg = 'childMsg hello';

defineExpose({ handleAlert, childMsg });

const cur = getCurrentInstance();
onMounted(() => {
  console.log(
    '%c [ cur ]-30',
    'font-size:13px; background:pink; color:#bf2c9f;',
    cur?.parent?.exposed.child2.value.inputValue
  );
});
</script>

<style lang="less" scoped></style>
