<script setup>

import {ref} from "vue";
const searchTerm = ref('')
defineProps(["books"])

function searchBooks(){
   fetch( `http://localhost:5173/books/title=${searchTerm.value}`,{
    method: 'GET',
    headers: {
      'Content-Type': 'application/json'
    }
   }).then(res => res.json()).then(data => books.value = data)
}

</script>

<template>
  <section>
    <div class="flex flex-row gap-2">
      <input v-model="searchTerm" type="text" placeholder="Search" class="bg-transparent border rounded-md focus:ring-0  w-full px-2 py-3" />
      <button @click="searchBooks()" class="bg-transparent border rounded-md focus:ring-0 px-2 py-3">Search</button>
    </div>

  </section>
</template>

<style scoped>

</style>