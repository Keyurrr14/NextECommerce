<template>
  <div class="p-10 w-full h-screen bg-zinc-800 text-white">
    <center>
      <transition name="fade1" >
        <h1 v-if="showText" class="text-5xl m-10">This is About Page</h1>
      </transition>
      <transition name="fade">
        <p v-if="showText" class="text-2xl">
          Lorem ipsum dolor sit amet, consectetur adipisicing elit. Dolor
          deleniti architecto hic ea rem, enim doloribus ducimus similique,
          labore distinctio sit tenetur error laudantium! Enim architecto optio
          exercitationem magnam autem unde, consequatur, delectus quisquam ea
          quas dicta! Ex officia quaerat modi minima voluptate repellat incidunt
          maiores nihil? Soluta, ex doloremque.
        </p>
      </transition>
    </center>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const showText = ref(false);

onMounted(() => {
  showText.value = true;
});
</script>

<style>
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
.fade-enter-to,
.fade-leave-from {
  opacity: 1;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 4s ease;
}

.fade1-enter-from,
.fade1-leave-to {
  opacity: 0;
}
.fade1-enter-to,
.fade1-leave-from {
  opacity: 1;
}
.fade1-enter-active,
.fade1-leave-active {
  transition: opacity 4s ease;
}
</style>
