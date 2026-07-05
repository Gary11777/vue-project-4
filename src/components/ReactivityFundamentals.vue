<script setup>
import { ref, onUnmounted } from 'vue'

const count = ref(0)
const message = ref('')

let messageTimer = null

function showMessage(text) {
  message.value = text

  if (messageTimer) {
    clearTimeout(messageTimer)
  }

  messageTimer = setTimeout(() => {
    message.value = ''
    messageTimer = null
  }, 3000)
}

onUnmounted(() => {
  if (messageTimer) clearTimeout(messageTimer)
})

function increment() {
  if (count.value < 5) {
    count.value++
  } else {
    showMessage('You can not add more than 5 items.')
  }
}

function decrement() {
  if (count.value > 0) {
    count.value--
    message.value = ''
    if (messageTimer) {
      clearTimeout(messageTimer)
      messageTimer = null
    }
  }
}

function reset() {
  count.value = 0
  message.value = ''
  if (messageTimer) {
    clearTimeout(messageTimer)
    messageTimer = null
  }
}
</script>

<template>
  <header class="page-header">
    <h1>Reactivity Fundamentals</h1>
    <p>Count: {{ count }} <span v-if="message" class="message">{{ message }}</span></p>
    <button @click="increment">Increment</button>
    <button @click="decrement">Decrement</button>
    <button @click="reset">Reset</button>
  </header>
</template>

<style scoped>
.message {
  color: red;
  margin-top: 1rem;
}
</style>
