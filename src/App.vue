<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" :top="top" :left="left" @end="endGame"/>
  <Results v-if="showResults" :score="score"/>
</template>

<script setup>

import {ref} from "vue";
import Block from "@/components/Block"
import Results from "@/components/Results"

let isPlaying = ref(false)
let delay = ref(null)
let top = ref(0)
let left = ref(0)
let score = ref(null)
let showResults = ref(false)

function start() {
  isPlaying.value = true
  delay.value=2000+Math.random()*5000
  top.value = 20+Math.random()*20
  left.value = Math.random()*50
  console.log('top is: ',top.value)
  showResults.value = false
}

function endGame(reactionTime){
  score.value = reactionTime
  showResults.value = true
  isPlaying.value = false
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
button {
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
