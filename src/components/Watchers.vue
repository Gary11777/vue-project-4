<script setup>
import { ref, watch } from 'vue'

const question = ref('')
const answer = ref('Questions usually contain a question mark. ;-)')
const loading = ref(false)

const x = ref(0)
const y = ref(0)

// watch works directly on a ref
watch(question, async (newQuestion, oldQuestion) => {
  if (newQuestion.includes('?')) {
    loading.value = true
    answer.value = 'Thinking...'
    try {
      const res = await fetch('https://yesno.wtf/api')
      answer.value = (await res.json()).answer
    } catch (error) {
      answer.value = 'Error! Could not reach the API. ' + error
    } finally {
      loading.value = false
    }
  }
})

// single ref
watch(x, (newX) => {
  console.log(`x is ${newX}`)
})

// getter
watch(
  () => x.value + y.value,
  (sum) => {
    console.log(`sum of x and y is: ${sum}`)
  }
)

// array of multiple sources
watch([x, () => y.value], ([newX, newY]) => {
  console.log(`x is ${newX} and y is ${newY}`)
})
</script>

<template>
  <section class="container">
    <header class="page-header">
        <h1 class="underline">Watchers</h1>
    </header>

    <div class="box">
      <p>
        Ask a yes/no question:
        <input v-model="question" :disabled="loading" />
      </p>
      <p>{{ answer }}</p>
    </div>

    <div class="box">
      <p>x: {{ x }}, y: {{ y }}, sum: {{ x + y }}</p>
      <p>
        Set x:
        <input type="number" v-model.number="x" />
      </p>
      <p>
        Set y:
        <input type="number" v-model.number="y" />
      </p>
    </div>
  </section>
</template>

<style scoped>
.box {
  border: 1px solid;
  padding: 2rem;
}
</style>