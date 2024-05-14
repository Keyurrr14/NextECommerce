<template>
    <div class="grid grid-cols-2 gap-5 p-14">
        <div class=" w-full h-3/5 overflow-hidden rounded-lg">
            <img :src="product.image" alt="" class="w-full h-full object-contain">
        </div>
        <div class="text-white mt-10">
            <h1 class="font-bold text-3xl">{{ product.title }}</h1>
            <h3 class="text-2xl mt-4">Price: ${{ product.price }}</h3>
            <p class="text-md mt-4">{{ product.description }}</p>
        </div>
    </div>
</template>


<script setup>
    const {product} = defineProps(["product"])
</script>


<style scoped></style>
