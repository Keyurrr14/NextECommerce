<template>
  <div class="grid grid-cols-2 gap-5 p-14">
    <div class="w-full h-3/5 overflow-hidden rounded-lg">
      <img :src="product.image" alt="" class="w-full h-full object-contain" />
    </div>
    <div class="text-white mt-10">
      <h1 class="font-bold text-3xl title">{{ product.title }}</h1>
      <h3 class="text-2xl mt-4">Price: ${{ product.price }}</h3>
      <h3 :class="priceColor" class="text-2xl mt-4 text-flicker-out-glow">
        Discounted Price: ${{ discountedPrice }}
      </h3>
      <!-- Rounded to 2 decimal places -->
      <p class="text-md mt-4 text-focus-in">{{ product.description }}</p>
    </div>
  </div>
</template>

<script setup>
const { product: productProp } = defineProps(["product"]);

import { ref, computed, watch } from "vue";

const product = ref(productProp);

const discountedPrice = computed(() => {
  if (product.value) {
    return (product.value.price * 0.8).toFixed(2);
  } else {
    return product.value;
  }
});

let previousPrice = productProp.price;

watch(
  () => productProp,
  (newValue, oldValue) => {
    if (newValue.price !== previousPrice) {
      previousPrice = newValue.price;
      updatePriceColor(newValue.price);
    }
  }
);

const priceColor = ref("text-green-500");

function updatePriceColor(newPrice) {
  priceColor.value =
    newPrice > previousPrice ? "text-red-500" : "text-green-500";
}
</script>

<style scoped>
.title {
  display: inline-block;
  border-right: 5px solid;
  width: 100%;
  white-space: nowrap;
  overflow: hidden;
  animation: typing 2s , cursor 0.4s step-end infinite alternate;
}
.text-focus-in {
	-webkit-animation: text-focus-in 1s cubic-bezier(0.550, 0.085, 0.680, 0.530) both;
	        animation: text-focus-in 1s cubic-bezier(0.550, 0.085, 0.680, 0.530) both;
}
.text-flicker-out-glow {
	-webkit-animation: text-flicker-out-glow 2.5s linear both;
	        animation: text-flicker-out-glow 2.5s linear both;
}
.shadow-pop-bl {
	-webkit-animation: shadow-pop-bl 0.3s cubic-bezier(0.470, 0.000, 0.745, 0.715) both;
	        animation: shadow-pop-bl 0.3s cubic-bezier(0.470, 0.000, 0.745, 0.715) both;
}
 @-webkit-keyframes text-flicker-out-glow {
  0% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.6), 0 0 60px rgba(255, 255, 255, 0.45), 0 0 110px rgba(255, 255, 255, 0.25), 0 0 100px rgba(255, 255, 255, 0.1);
  }
  13.9% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.6), 0 0 60px rgba(255, 255, 255, 0.45), 0 0 110px rgba(255, 255, 255, 0.25), 0 0 100px rgba(255, 255, 255, 0.1);
  }
  14% {
    opacity: 0;
    text-shadow: none;
  }
  14.9% {
    opacity: 0;
    text-shadow: none;
  }
  15% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.55), 0 0 60px rgba(255, 255, 255, 0.4), 0 0 110px rgba(255, 255, 255, 0.2), 0 0 100px rgba(255, 255, 255, 0.1);
  }
  22.9% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.55), 0 0 60px rgba(255, 255, 255, 0.4), 0 0 110px rgba(255, 255, 255, 0.2), 0 0 100px rgba(255, 255, 255, 0.1);
  }
  23% {
    opacity: 0;
    text-shadow: none;
  }
  24.9% {
    opacity: 0;
    text-shadow: none;
  }
  25% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.55), 0 0 60px rgba(255, 255, 255, 0.35), 0 0 100px rgba(255, 255, 255, 0.1);
  }
  34.9% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.55), 0 0 60px rgba(255, 255, 255, 0.35), 0 0 100px rgba(255, 255, 255, 0.1);
  }
  35% {
    opacity: 0;
    text-shadow: none;
  }
  39.9% {
    opacity: 0;
    text-shadow: none;
  }
  40% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.55), 0 0 60px rgba(255, 255, 255, 0.35);
  }
  42.9% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.55), 0 0 60px rgba(255, 255, 255, 0.35);
  }
  43% {
    opacity: 0;
    text-shadow: none;
  }
  44.9% {
    opacity: 0;
    text-shadow: none;
  }
  45% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.45), 0 0 60px rgba(255, 255, 255, 0.25);
  }
  50% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.45), 0 0 60px rgba(255, 255, 255, 0.25);
  }
  54.9% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.45), 0 0 60px rgba(255, 255, 255, 0.25);
  }
  55% {
    opacity: 0;
    text-shadow: none;
  }
  69.4% {
    opacity: 0;
    text-shadow: none;
  }
  69.5% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.45), 0 0 60px rgba(255, 255, 255, 0.25);
  }
  69.9% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.45), 0 0 60px rgba(255, 255, 255, 0.25);
  }
  70% {
    opacity: 0;
    text-shadow: none;
  }
  79.4% {
    opacity: 0;
    text-shadow: none;
  }
  79.9% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.25);
  }
  80% {
    opacity: 0;
    text-shadow: none;
  }
  89.8% {
    opacity: 0;
    text-shadow: none;
  }
  89.9% {
    opacity: 1;
    text-shadow: none;
  }
  90% {
    opacity: 0;
    text-shadow: none;
  }
  100% {
    opacity: 0;
  }
}
@keyframes text-flicker-out-glow {
  0% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.6), 0 0 60px rgba(255, 255, 255, 0.45), 0 0 110px rgba(255, 255, 255, 0.25), 0 0 100px rgba(255, 255, 255, 0.1);
  }
  13.9% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.6), 0 0 60px rgba(255, 255, 255, 0.45), 0 0 110px rgba(255, 255, 255, 0.25), 0 0 100px rgba(255, 255, 255, 0.1);
  }
  14% {
    opacity: 0;
    text-shadow: none;
  }
  14.9% {
    opacity: 0;
    text-shadow: none;
  }
  15% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.55), 0 0 60px rgba(255, 255, 255, 0.4), 0 0 110px rgba(255, 255, 255, 0.2), 0 0 100px rgba(255, 255, 255, 0.1);
  }
  22.9% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.55), 0 0 60px rgba(255, 255, 255, 0.4), 0 0 110px rgba(255, 255, 255, 0.2), 0 0 100px rgba(255, 255, 255, 0.1);
  }
  23% {
    opacity: 0;
    text-shadow: none;
  }
  24.9% {
    opacity: 0;
    text-shadow: none;
  }
  25% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.55), 0 0 60px rgba(255, 255, 255, 0.35), 0 0 100px rgba(255, 255, 255, 0.1);
  }
  34.9% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.55), 0 0 60px rgba(255, 255, 255, 0.35), 0 0 100px rgba(255, 255, 255, 0.1);
  }
  35% {
    opacity: 0;
    text-shadow: none;
  }
  39.9% {
    opacity: 0;
    text-shadow: none;
  }
  40% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.55), 0 0 60px rgba(255, 255, 255, 0.35);
  }
  42.9% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.55), 0 0 60px rgba(255, 255, 255, 0.35);
  }
  43% {
    opacity: 0;
    text-shadow: none;
  }
  44.9% {
    opacity: 0;
    text-shadow: none;
  }
  45% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.45), 0 0 60px rgba(255, 255, 255, 0.25);
  }
  50% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.45), 0 0 60px rgba(255, 255, 255, 0.25);
  }
  54.9% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.45), 0 0 60px rgba(255, 255, 255, 0.25);
  }
  55% {
    opacity: 0;
    text-shadow: none;
  }
  69.4% {
    opacity: 0;
    text-shadow: none;
  }
  69.5% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.45), 0 0 60px rgba(255, 255, 255, 0.25);
  }
  69.9% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.45), 0 0 60px rgba(255, 255, 255, 0.25);
  }
  70% {
    opacity: 0;
    text-shadow: none;
  }
  79.4% {
    opacity: 0;
    text-shadow: none;
  }
  79.9% {
    opacity: 1;
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.25);
  }
  80% {
    opacity: 1;
    text-shadow: none;
  }
  89.8% {
    opacity: 1;
    text-shadow: none;
  }
  89.9% {
    opacity: 1;
    text-shadow: none;
  }
  90% {
    opacity: 1;
    text-shadow: none;
  }
  100% {
    opacity: 1;
  }
}

 @-webkit-keyframes text-focus-in {
  0% {
    -webkit-filter: blur(12px);
            filter: blur(12px);
    opacity: 0;
  }
  100% {
    -webkit-filter: blur(0px);
            filter: blur(0px);
    opacity: 1;
  }
}
@keyframes text-focus-in {
  0% {
    -webkit-filter: blur(12px);
            filter: blur(12px);
    opacity: 0;
  }
  100% {
    -webkit-filter: blur(0px);
            filter: blur(0px);
    opacity: 1;
  }
}

@keyframes cursor {
    from,
  to {
    border-color: transparent;
  }
  50% {
    border-color: white;
  }
}
@keyframes typing {
  from {
    width: 0;
  }
  to {
    width: 100%;
  }
}
</style>
