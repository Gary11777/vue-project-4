<script setup>
defineProps(['title'])
defineEmits(['enlarge-text', 'reset-text'])
</script>

<template>
  <div class="blog-post">
    <h4>{{ title }}</h4>
    <button @click="$emit('enlarge-text')">Enlarge text</button>
    <button @click="$emit('reset-text')">Reset text</button>
  </div>
</template>