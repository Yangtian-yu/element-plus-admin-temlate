<template>
  <button @click="changeMes">change</button>

  <div>{{ message }}</div>
</template>

<script setup lang="ts">
import { customRef } from "vue";

function MyRef<T>(value: T) {
  return customRef((trank, trigger) => {
    return {
      get() {
        trank();
        return value;
      },
      set(newValue: T) {
        console.log("set");
        value = newValue;
        trigger();
      },
    };
  });
}

let message = MyRef<string>("小");
const changeMes = function () {
  message.value = "大";
};
</script>
<style scoped></style>
