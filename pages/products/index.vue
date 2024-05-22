<template>
  <div class="w-full min-h-screen bg-zinc-800">
    <div class="flex justify-end p-5">
      <select v-model="sortOrder" @change="sortProducts" class="bg-zinc-700 text-white p-2 rounded-lg">
        <option value="asc">Price: Low to High</option>
        <option value="desc">Price: High to Low</option>
      </select>
    </div>
    <div class="grid grid-cols-4 gap-5 p-16 pt-0 text-white">
      <div v-for="p in sortedProducts" :key="p.id">
        <ProductCard :product="p" />
      </div>
    </div>
  </div>
</template>


<script setup>
import { ref, computed, onMounted } from 'vue';

const products = ref([]);
const sortOrder = ref('asc');

const fetchProducts = async () => {
  try {
    const response = await fetch('https://fakestoreapi.com/products');
    const data = await response.json();
    products.value = data;
  } catch (error) {
    console.error('Failed to fetch products:', error);
  }
};

onMounted(fetchProducts);

const sortProducts = () => {
  products.value = products.value.slice().sort((a, b) => {
    if (sortOrder.value === 'asc') {
      return a.price - b.price;
    } else {
      return b.price - a.price;
    }
  });
};

const sortedProducts = computed(() => {
  return products.value;
});

watchEffect(sortProducts);
</script>

<style scoped></style>
