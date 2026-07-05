<script setup>
import { reactive, computed } from 'vue'

const author = reactive({
  name: 'John Doe',
  books: [
    'Vue 2 - Advanced Guide',
    'Vue 3 - Basic Guide',
    'Vue 4 - The Mystery'
  ]
})

// a computed ref
const publishedBooksMessage = computed(() => {
  return author.books.length > 0 ? 'Yes' : 'No'
})
</script>
    
<template>
  <header class="page-header">
    <h1>Computed Properties</h1>
    <p>Has published books: <span>{{ publishedBooksMessage }}</span></p>
    
  </header>
</template>