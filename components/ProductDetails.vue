<template>
    <div class="grid grid-cols-2 gap-5 p-14">
        <div class=" w-full h-3/5 overflow-hidden rounded-lg">
            <img :src="product.image" alt="" class="w-full h-full object-contain">
        </div>
        <div class="text-white mt-10">
            <h1 class="font-bold text-3xl">{{ product.title }}</h1>
            <h3 class="text-2xl mt-4">Price: ${{ product.price }}</h3>
            <h3 :class="priceColor" class="text-2xl mt-4">Discounted Price: ${{ discountedPrice }}</h3> <!-- Rounded to 2 decimal places -->
            <p class="text-md mt-4">{{ product.description }}</p>
        </div>
    </div>
</template>

<script setup>
    const { product: productProp } = defineProps(["product"]); 

    import { ref, computed, watch } from 'vue';

    const product = ref(productProp); 

    const discountedPrice = computed(() => {
        if (product.value) {
            return (product.value.price * 0.8).toFixed(2); 
        } else {
            return product.value;
        }
    });


    let previousPrice = productProp.price;


    watch(() => productProp, (newValue, oldValue) => {

        if (newValue.price !== previousPrice) {
            previousPrice = newValue.price;
            updatePriceColor(newValue.price);
        }
    });

    const priceColor = ref('text-green-500'); 

    function updatePriceColor(newPrice) {
        priceColor.value = newPrice > previousPrice ? 'text-red-500' : 'text-green-500';
    }
</script>

<style scoped></style>
