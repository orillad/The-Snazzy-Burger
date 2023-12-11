<template>
    <div>
      <h1>{{ textCamp }}</h1>
      <input v-model="textCamp" />
      <button >Place Order</button>
    </div>
  </template>
  
  <script setup lang="ts">
  import { ref } from 'vue';
  
  const textCamp = ref('The Snazzy Burger');
  

  </script>
  