<script setup>
import { ref } from 'vue'

const message = ref('')
const multi_line_message = ref('')
const checked = ref(true)
const picked = ref('yes')
const checkedNames = ref([])
const selected = ref('')
</script>

<template>
  <section class="container">
    <header class="page-header">
        <h1 class="underline">Form Input Bindings</h1>
    </header>

    <p>Message is: {{ message }}</p>
    <input v-model="message" placeholder="Enter your message" />

    <span>Multiline message is:</span>
    <p style="white-space: pre-line;">{{ multi_line_message }}</p>
    <textarea v-model="multi_line_message" placeholder="Add a new todo" />

    
    <label><input type="checkbox" v-model="checked" /> {{ checked }}</label>

    
    <label>Yes <input type="radio" value="yes" v-model="picked" /></label>
    <label>No <input type="radio" value="no" v-model="picked" /></label>
    <p>Picked: {{ picked }}</p>

    <div>Checked names: {{ checkedNames }}</div>
    <label for="Jack">Jack <input type="checkbox" value="Jack" v-model="checkedNames" /></label>
    <label for="John">John <input type="checkbox" value="John" v-model="checkedNames" /></label>
    <label for="Mike">Mike <input type="checkbox" value="Mike" v-model="checkedNames" /></label>

    <div>Selected: {{ selected }}</div>
    <select v-model="selected">
      <option disabled value="">Please select one</option>
      <option value="One">One</option>
      <option value="Two">Two</option>
      <option value="Three">Three</option>
    </select>

  </section>
</template>