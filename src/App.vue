<script setup lang="ts">
import { $ref } from 'vue/macros';
import arrow from '~/assets/images/arrow.svg';

let email = $ref('');
let error = $ref(0);

const submit = () => {
  if (/([\w\d.]+)@\w+\.\w+/.test(email)) {
    error = -1;
  } else {
    error = 1;
  }
}
</script>

<template>
  <div class="flex items-center justify-center h-screen text-[#32475b]">
    <form @submit.prevent="submit">
      <h1 class="text-3xl font-bold mb-8">
        Sign up from the <br/> latest updates
      </h1>
      <p class="uppercase font-semibold text-[#3fb27f] text-sm">email address</p>
      <div class="border-1 hover:border-[#3fb27f]">
        <input v-model="email" class="px-2">
        <button class="bg-[#3fb27f] h-10 px-3">
          <img :src="arrow" alt="">
        </button>
      </div>
      <div v-if="error === 1" class="border-1 border-[#B71540] text-[#B71540] bg-[#FDEFF3] p-4 mt-4">
        <h1 class="font-semibold">Please use a valid email</h1>
        <p class="text-sm">Like: person@inbox.com</p>
      </div>
      <div v-else-if="error === -1" class="border-1 border-[#258A85] text-[#258A85] bg-[#F5FFFE] p-4 mt-4">
        <h1 class="font-semibold">Yay! Thank you</h1>
        <p class="text-sm">We've send a confirmation <br /> link to your inbox</p>
      </div>
    </form>
  </div>
</template>
