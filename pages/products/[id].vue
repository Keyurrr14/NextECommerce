<template>
  <div class="w-full h-screen bg-zinc-800">
    <h1>{{ product.title }}</h1>
    <h1>{{ product.price }}</h1>
    <h1>{{ product.id }}</h1>
  </div>
</template>

<script setup>
    const { id } = useRoute().params
    const url = "https://fakestoreapi.com/products/" + id

    const { data : product } = await useFetch(url)
</script>

<style scoped></style>
