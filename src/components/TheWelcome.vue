<script setup>
import { ref } from 'vue'

const advice = ref([])
const url = ref("	https://api.adviceslip.com/advice")

const getAdvice = async()=>{
  try {
    const res = await fetch(url.value)
    let data = await res.json()


    console.log(data);
    advice.value = data 
    console.log(advice.value);

  } catch (error) {
    
  }

}

getAdvice()


</script>

<template>
<main class="h-screen flex bg-[#1f2632] px-4">
  <div v-for="item in advice" :key="item.id" class=" shadow-2xl relative flex flex-col gap-6 p-8 m-auto rounded-lg w-full max-w-[400px] text-[#cee3e9] bg-[#323a49] text-center">
    <h2 class="text-sm text-[#52ffa8]">ADVICE  #{{ item.id }}</h2>
    <p class=" text-[20px]">"{{ item.advice }}"</p>
    <img class="z-50 mb-8" src="../assets/images/pattern-divider-desktop.svg" alt="Divider">
    <button @click="getAdvice" class=" shadow-xl absolute bottom-[-1.5rem] left-[45%] w-fit rounded-full p-3 bg-[#52ffa8]">
      <img class="" src="../assets/images/icon-dice.svg" alt="">
    </button>
  </div>
</main>

</template>
