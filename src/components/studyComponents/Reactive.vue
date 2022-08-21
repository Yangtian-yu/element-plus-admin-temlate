<template>
  <div>
    <button @click="chanage1">chanage1</button>
    <button @click="chanage2">chanage2</button>
    <div>arr{{ message }}</div>
    <div>object{{ obj }}</div>
    <div>{{ messageinfo }}</div>
  </div>
</template>

<script setup lang="ts">
import { reactive, readonly, shallowReactive } from "vue";

let message = reactive<number[]>([]);
let obj = reactive({
  name: "sssss",
});
obj.name = "888";
setTimeout(() => {
  let arr = [1, 2, 3, 4];
  message.push(...arr);
}, 1000);

let person = reactive({
  count: 1,
});
let copy = readonly(person);
// copy.count++;

let messageinfo = shallowReactive({
  test: "sss",
  nav: {
    bar: {
      name: "我我我哦",
    },
  },
});

const chanage1 = () => {
  messageinfo.test = "我被改了";
};
const chanage2 = () => {
  messageinfo.nav.bar.name = "我也被改啦";
};
</script>

<style scoped></style>
