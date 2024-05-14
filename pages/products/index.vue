<template>
  <div class="w-full h-screen bg-zinc-800">
    <div class="grid grid-cols-4 gap-5 p-16 text-white ">
        <div v-for="p in products">
            <NuxtLink :to="`/products/${p.id}`">{{ p.title }}</NuxtLink>
        </div>
    </div>
  </div>
</template>

<script setup>
    const { data : products } = await useFetch("https://fakestoreapi.com/products");
</script>

<style scoped></style>
