<template>
<div class="block" v-if="showBlock" @click="stopTimer" :style="{top: topPosistion, left: leftPosistion}">
  click me {{delay}}


</div>
</template>


<script setup>
import {computed, onUpdated, ref} from "vue";
import {defineProps, onMounted} from "vue";

const emits = defineEmits(['end'])

const topPosistion = computed(()=>{
  return stylePosition(props.top)
})

const leftPosistion = computed(()=>{
  return stylePosition(props.left)
})


function stylePosition(pos){
  return pos+"%"
}
const props = defineProps({
  delay: Number,
  top: Number,
  left: Number

})
let showBlock = ref(false)

function startTimer() {
  timer = setInterval(()=>{
    reactionTime.value += 10
  },10)
}

function stopTimer() {
 clearInterval(timer)
  console.log("REACTION TIME IS: ",reactionTime.value)
  emits('end',reactionTime.value)
}

let timer = null
let reactionTime = ref(0)

onMounted(()=>{
  console.log(topPosistion.value)
  setTimeout(()=>{
    showBlock.value = true
    startTimer()
  },props.delay-1000)
})

onUpdated(()=>{
  console.log('UPDATED BLOCK COMPONENT')
})
</script>

<style scoped>
  .block {
    position: absolute;
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
  }
</style>
