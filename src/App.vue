<script setup>
import { onMounted, ref } from "vue";
import axios from "axios"

const products = ref ([])

const fetchAllProduct = async () => {
  const reponse = await axios.get("https://https://fakestoreapi.com/products")
  products.value = reponse.data 

  onMounted(async () => fetchAllProduct() )
}
</script>

<template>

  <h1>Welcome to fake e-store!</h1>
  <div class="grid grid-cols-4 gap-4"></div>
  <article v-for="product in products" :key="product.id">
    <img class="w-full aspect-video object-contain" :src="product.img" alt="">
    <h4>{{ product.title }}</h4>

  </article>
  
</template>