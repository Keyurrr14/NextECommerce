<template>
  <div class="w-full min-h-screen bg-zinc-800">
    <ProductDetails :product = "product"/>
  </div>
</template>

<script setup>
    const { id } = useRoute().params
    const url = "https://fakestoreapi.com/products/" + id

    const { data : product } = await useFetch(url)
</script>

<style scoped></style>
