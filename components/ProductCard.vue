<template>
    <div class="p-3 rounded-lg bg-zinc-900 h-full text-center">
        <div class="w-full h-52 overflow-hidden rounded-lg">
            <img :src="product.image" class="w-full h-full object-contain" alt="">
        </div>
        <p class="font-3xl text-white font-bold">{{ product.title }}</p>
        <NuxtLink :to="`/products/${product.id}`">
            <p class="bg-[#12b188] text-white px-3 py-2 rounded-lg text-sm my-5">View Details</p>
        </NuxtLink>

    </div>
</template>


<script setup>
    const {product} = defineProps(["product"])
</script>


<style scoped></style>
