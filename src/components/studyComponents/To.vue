<template>
  <div>
    <div><button @click="change">該表</button></div>
    <div>{{ state }}</div>
    <div>{{ foo }}</div>
  </div>
</template>

<script setup lang="ts">
import { toRef, reactive, toRefs, toRaw } from "vue";
const obj = reactive({
  foo: 1,
  bar: 1,
});
const state = toRef(obj, "bar");
const change = () => {
  state.value++;
  console.log("----原始對象", obj);
  console.log("---引用對象", state);
  foo.value++;
};

let obj1 = reactive({
  foo: 1,
  bar: 1,
});

let { foo, bar } = toRefs(obj1); //避免結構賦值后失去响应式

let obj2 = reactive({
  foo: 1,
  bar: 1,
});
const raw = toRaw(obj);
console.log("响应式的", obj2);
console.log("raw", raw); //响应式改为非响应式
</script>

<style scoped></style>
