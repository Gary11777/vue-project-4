<script setup>
import { ref } from 'vue'

const awesome = ref(true)
</script>

<template>

    <section class="container">
        <header class="page-header">
            <h1 class="underline">Conditional Rendering</h1>
        </header>

        <div class="demo-container">
            <p v-if="awesome">Vue is awesome!</p>
            <p v-else>Vue is not awesome.</p>
            <button @click="awesome = !awesome">
                Toggle awesome
            </button>
        </div>
    </section>

</template>