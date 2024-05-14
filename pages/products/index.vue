<template>
  <div class="w-full min-h-screen bg-zinc-800">
    <div class="grid grid-cols-4 gap-5 p-16 text-white ">
        <div v-for="p in products">
          <ProductCard :product="p"/>
        </div>
    </div>
  </div>
</template>

<script setup>
    const { data : products } = await useFetch("https://fakestoreapi.com/products");
</script>

<style scoped></style>
