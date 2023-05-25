<script setup>
import Child1 from './components/Child1.vue';
import Child2 from './components/Child2.vue';
import { ref, onMounted, provide } from 'vue';
defineOptions({
  name: 'App',
});
const msg = ref('Hello');

const handleChangeMsg = (value) => {
  msg.value = value;
};
const child1 = ref(null);
const child2 = ref(null);

const handleAlert = () => {
  child1.value.handleAlert();
};

const childMsg = ref('');

onMounted(() => {
  childMsg.value = child1.value.childMsg;
});

const provideValue = ref('provide value12112212');
provide('provideKey', provideValue);

defineExpose({ child2 });
</script>

<template>
  <Child1 :msg="msg" ref="child1" age="20" class="ChildClass1" name="child1" />
  <Child2 :msg="msg" @handleChangeMsg="handleChangeMsg" ref="child2" />
  <div>
    <button @click="handleAlert">parent alert</button>

    {{ childMsg }}
  </div>
</template>
