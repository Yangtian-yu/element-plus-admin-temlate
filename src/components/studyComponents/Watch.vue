<template>
  <div>
    <input type="text" v-model="message.name" />
    <input type="text" v-model="message2" />
    <input type="text" v-model="message3" id="ipt" />
    <input type="text" v-model="message4" />
    <button @click="stopWtch">停止监听</button>
  </div>
</template>

<script setup lang="ts">
import { ref, watch, reactive, watchEffect } from "vue";
let message = reactive({
  name: "",
});
let message2 = ref<string>("");
watch(
  () => message.name,
  (newval, oldValue) => {
    console.log("新" + newval);
    console.log("旧" + oldValue);
  },
  {
    deep: true,
  }
);
let message3 = ref<string>("飞机");
let message4 = ref<string>("飞机坏了");
const stop = watchEffect(
  (anivalidata) => {
    // let ipt: HTMLInputElement = document.querySelector(
    //   "#ipt"
    // ) as HTMLInputElement;
    // console.log(ipt, "ipt");
    console.log("message====>", message3.value);
    // console.log("message====>", message4.value);
    anivalidata(() => {
      console.log("before");
    });
  },
  {
    flush: "post",
    onTrigger(e) {
      debugger;
    },
  }
);
//停止监听
const stopWtch = function () {
  stop();
};
</script>

<style scoped></style>
