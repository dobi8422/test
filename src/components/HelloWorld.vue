<script setup>
import { ref } from 'vue'
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
const getToken = () => {
  messageHandler?.postMessage(JSON.stringify(action[0]));
  console.log(JSON.stringify(action[0]));
}
const onOffPage = () => {
  messageHandler?.postMessage(JSON.stringify(action[1]));
  console.log(JSON.stringify(action[1]));
}
</script>

<template>
  <ul>
    <li>token: {{ token || "nothing" }}</li>
    <hr>
    <button @click="getToken">action: getToken</button>
    <button @click="onOffPage">action: offPage</button>
    <hr>
    <li>{{ device }}</li>
    <hr>
    <li>{{ app }}</li>
    <hr>
    <li>{{ ua }}</li>
  </ul>
</template>
