<script setup>
import { ref } from 'vue'
import BlogPost from '@/components/BlogPost.vue'
import AlterBox from '@/components/AlterBox.vue'


const posts = ref([
  { id: 1, title: 'My journey with Vue' },
  { id: 2, title: 'Blogging with Vue' },
  { id: 3, title: 'Why Vue is so fun' }
])

const postFontSize = ref(1)

const count = ref(0)
</script>

<template>
    <section class="container">
      <header class="page-header">
        <h1 class="underline">Component Basics</h1>
      </header>

      <div class="box">
        <button @click="count++">You clicked me {{ count }} times.</button>
      </div>
      <div class="box">
        <h2>Blog Posts</h2>
        <BlogPost title="My journey with Vue" />
        <BlogPost title="Blogging with Vue" />
        <BlogPost title="Why Vue is so fun" />
      </div>
      <div class="box" :style="{ fontSize: postFontSize + 'em' }">
        <h2>Blog Posts (an array of posts)</h2>
        <BlogPost 
            v-for="post in posts" 
            :key="post.id" 
            :title="post.title" 
            @enlarge-text="postFontSize += 0.1"
            @reset-text="postFontSize = 1"
        />
      </div>
      <div class="box">
        <AlterBox>
          <h2>Error</h2>
          <p>Something went wrong</p>
        </AlterBox>
      </div>
    </section>
  </template>