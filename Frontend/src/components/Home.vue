<template>
  <section>
    <section class="h-72 bg-cover bg-center flex flex-col items-center justify-center" :style="{ backgroundImage: `url('${path}')` }">
      <h1 class="text-5xl z-10 text-white">
        Experience the joy of reading
      </h1>
    </section>
    <section class="h-72 flex flex-col justify-center items-center ">
      <h2 class="text-3xl mb-4 font-normal text-transparent bg-clip-text bg-gradient-to-r from-neutral-300 to-green-900">Welcome to Our Bookstore</h2>
      <p class="text-lg mb-2">Explore our collection of books</p>
      <p class="italic text-gray-600">Curated by our team of experts</p>
    </section>
  </section>
</template>

<script setup>
const path = 'https://i.pinimg.com/564x/c2/c8/9d/c2c89ddf46d8237e395e301f5a020943.jpg'
</script>

<style scoped>
/* You can add any custom scoped styles here */
</style>
