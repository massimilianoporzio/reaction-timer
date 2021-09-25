<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start">Play</button>
</template>

<script setup>

import {ref} from "vue";

let isPlaying = ref(false)
let delay = ref(null)

function start() {
  isPlaying.value = true
  delay.value=2000+Math.random()*5000
  console.log('delay is: ',delay.value)
}


</script>



<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
</style>
