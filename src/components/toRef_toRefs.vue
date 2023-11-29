<script setup lang="ts">
import { reactive, toRef, toRefs, toRaw } from 'vue';


const man = reactive({
  name: 'John',
  age: 28,
  job: 'Frontend'
})

//const name = toRef(man, 'name')
const { name, age, job } = toRefs(man)

const chengtoRefsBtn = () => {
  name.value = 'Chen yu sheng'
  age.value = 18
  job.value = 'Backend'
}



</script> 

<template>
  <div>
     {{name}} === {{age}} === {{job}} 
    <button @click="chengtoRefsBtn"></button>

  </div>
</template>

<style scoped></style>
