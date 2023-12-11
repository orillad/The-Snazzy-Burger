<!-- Cart.vue -->
<template>
    <div>
      <h2>Shopping Cart</h2>
      <div>
        <label for="currency">Select Currency:</label>
        <select id="currency" v-model="selectedCurrency">
          <option value="USD">$ Dollars</option>
          <option value="EUR">€ Euros</option>
        </select>
      </div>
      <ul>
        <li v-for="(product, index) in products" :key="index">
          {{ product.name }} - {{ formatPrice(product.price) }}
          <button @click="addToCart(product)">Add to Cart</button>
        </li>
      </ul>
    </div>
  </template>
  
  <script setup lang="ts">
  import { ref } from 'vue';
  import type Product from '@/types/Products'
  
  const products = ref<Product[]>([
    { name: "Hamburger 🍔", price: 5 },
    { name: "Cheeseburger 🧀", price: 6 },
    { name: "Impossible Burger 🥕", price: 7 },
    { name: "Fries 🍟", price: 2 },
  ]);
  
  const cart = ref<Product[]>([]);
  const selectedCurrency = ref("USD");
  
  const addToCart = (product: Product) => {
    cart.value.push(product);
    const message = cart.value.map(p => `${p.name}`);
    alert(`Products added to the cart!\n\n${message}`);
  };
  
  
  const formatPrice = (price: number) => {
    if (selectedCurrency.value === "EUR") {
      return `€${(price * 0.85).toFixed(2)}`;
    } else {
      return `$${price.toFixed(2)}`;
    }
  };
  </script>
  
<style scoped>
    li{
        list-style: none;
    }
</style>