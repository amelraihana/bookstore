<template>
  <section class="py-8">
    <div class="flex flex-row gap-2">
      <input v-model="searchTerm" type="text" placeholder="Search" class="bg-transparent border rounded-md focus:ring-0  w-full px-2 py-3" />
      <button @click="searchBooks()" class="bg-transparent border rounded-md focus:ring-0 px-2 py-3">Search</button>
    </div>

    <div class="container mx-auto">
      <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-6">
        <div v-for="book in books" :key="book.id" class="bg-white rounded-lg shadow-md overflow-hidden">
          <div class="p-4">
            <h1 class="text-xl font-semibold mb-2">{{ book.Title }}</h1>
            <p class="text-gray-600 mb-2">{{ book.Author }}</p>
            <p class="text-green-600 font-semibold">{{ `${book.Price}` }}</p>
          </div>
          <img :src="`https://picsum.photos/200/300?random=${book.id}`" alt="Book Cover" class="w-full h-64 object-cover">
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { onMounted, ref } from 'vue'

const books = ref([])

const searchTerm = ref('')
defineProps(["books"])

function searchBooks(){
   fetch( `http://localhost:8080/books/title?title=${searchTerm.value}`,{
    method: 'GET',
    headers: {
      'Content-Type': 'application/json'
    }
   }).then(res => res.json()).then(data => books.value = data)
}

function getBooks() {
  fetch('http://localhost:8080/books', {
    method: 'GET',
    headers: {
      'Content-Type': 'application/json'
    }
  })
    .then(res => res.json())
    .then(data => (books.value = data))
}

onMounted(() => {
  getBooks()
})
</script>

<style scoped>
/* You can add any custom scoped styles here */
</style>
