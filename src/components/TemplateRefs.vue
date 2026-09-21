<script setup>
import { ref, useTemplateRef, onMounted } from 'vue'

// the first argument must match the ref value in the template
// const input = useTemplateRef('my-input')

const list = ref([1, 2, 3])

const itemRefs = useTemplateRef('items')

// onMounted(() => {
//   alert(itemRefs.value.map(i => i.textContent))
// })


// const focusInput = () => {
//   input.value.focus()
// // }

</script>

<template>
  <section class="container">
    <header class="page-header">
      <h1 class="underline">Template Refs</h1>
    </header>

    <div class="box">
      <input ref="my-input" />
      <!-- <button @click="focusInput">Focus input</button> -->
    </div>

    <ul>
        <li v-for="item in list" ref="items">
            {{ item }}
        </li>
    </ul>
  </section>
</template>
