<script setup>
import { ref } from 'vue'

const count = ref(0)

function say(message) {
  alert(message)
}

function warn(message, event) {
    if (event) {
        event.preventDefault()
    } 
    alert(message)
}
</script>

<template>
  <section class="container">
    <header class="page-header">
        <h1 class="underline">Event Handling</h1>
    </header>

    <button @click="warn('Form cannot be submitted yet.', $event)">Submit</button>
    <button @click="say('hello')">Say hello</button>
    <button @click="say('goodbye')">Say goodbye</button>
    <button @click="count++">Add 1</button>
    <p>Count is: {{ count }}</p>
  </section>
</template>