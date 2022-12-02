<script setup>
import { ref } from 'vue'
const timer = ref(0);
setInterval(() => timer.value++, 1000)

const action = [
  {
    action: "getToken",
  },
  {
    action: "offPage",
  },
];
const device = navigator.userAgent;
const app = navigator.appVersion;
const ua = navigator.userAgent.toLowerCase();
const token = ref();
const getAppUserToken = (arg) => {
  token.value = arg || "get token fail";
};

const token2 = ref();
const getAppUserToken2 = (arg) => {
  token2.value = arg || "get token fail";
};
let messageHandler;
setTimeout(() => {
  messageHandler?.postMessage(JSON.stringify(action[0]))
  console.log(JSON.stringify(action[0]));
}, 0);
setTimeout(() => getAppUserToken2(), 5000);
setTimeout(() => {
  messageHandler?.postMessage(JSON.stringify(action[1]))
  console.log(JSON.stringify(action[1]));
}, 10000);
</script>

<template>
  <ul>
    <li>time: {{ timer }}</li>
    <li>token: {{ token || "nothing" }}</li>
    <li>token2: {{ token2 || "nothing" }}</li>
    <hr>
    <li>{{ device }}</li>
    <hr>
    <li>{{ app }}</li>
    <hr>
    <li>{{ ua }}</li>
  </ul>
</template>
