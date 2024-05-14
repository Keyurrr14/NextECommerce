<template>
    <header class="bg-zinc-800 text-white  border-2 border-zinc-700">
        <nav class="px-16 py-5 flex justify-between items-center">
            <NuxtLink to="/" class="text-[#12b188] text-3xl font-bold">Click2Buy</NuxtLink>
            <ul class="flex gap-14">
                <li><NuxtLink to="/" class="text-xl font-medium">Home</NuxtLink></li>
                <li><NuxtLink to="/about" class="text-xl font-medium">About</NuxtLink></li>
                <li><NuxtLink to="/products" class="text-xl font-medium">Products</NuxtLink></li>
            </ul>
        </nav>
    </header>
</template>


<script setup>

</script>


<style scoped>
    .router-link-exact-active{
        color: #12b188;
    }
</style>

<!-- bg-[#12b188] text-white px-3 py-2 rounded-lg text-sm -->
