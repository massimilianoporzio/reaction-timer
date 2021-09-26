<template>
<p class="rank">{{ rank }} </p>
</template>

<script setup>

import {onMounted, ref} from "vue";

const props = defineProps(
    {
      score: Number
    }
)

let rank = ref(null)

onMounted(()=>{
  console.log('score value is ',props.score)
  if(props.score < 450){
    rank.value = "Ninja fingers!!!"
  }else if(props.score < 600){
    rank.value = "Rapid reflexes"
  }else{
    rank.value = "Snail pace..."
  }
})

</script>

<style scoped>
.rank {
  font-size: 1.4em;
  color: #0faf87;
  font-weight: bold;
}
</style>
