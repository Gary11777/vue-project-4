<script setup>
import Counter from '@/components/Counter.vue'
import CounterSummary from '@/components/CounterSummary.vue'
import ReactivityFundamentals from '@/components/ReactivityFundamentals.vue'
import ComputedProperties from '@/components/ComputedProperties.vue'
import ClassStyleBindings from '@/components/ClassStyleBindings.vue'
import ConditionalRendering from '@/components/ConditionalRendering.vue'
import ListRendering from '@/components/ListRendering.vue'
import TodoList from '@/components/TodoList.vue'
import { ref } from 'vue'

//Data
const dog_breeds = ref([
{label: 'Dalmatian', count: 0},
{label: 'Pug', count: 0},
{label: 'Beagle', count: 0, disabled: true},
{label: 'Poodle', count: 0},
{label: 'Bulldog', count: 0, disabled: true},
])

const handleIncrement = (breed, amount) => {
  breed.count += amount
}

const handleDecrement = (breed, amount) => {
  if (breed.count - amount >= 0) breed.count -= amount
}

const resetAllCounts = () => {
  dog_breeds.value.forEach(breed => {
    breed.count = 0
  })
}
</script>

<template>

  <!-- Components -->
  <TodoList />
  <ListRendering />
  <ConditionalRendering />
  <ClassStyleBindings />
  <ComputedProperties />
  <ReactivityFundamentals />

  <!-- Dog Park Counter -->
  <h1>Dog Park Counter</h1>
  <div class="breed-list">
  <Counter 
    v-for="breed in dog_breeds" 
    :label="breed.label" 
    :count="breed.count.toString()"
    :disabled="breed.disabled"
    @increment="amount => handleIncrement(breed, amount)"
    @decrement="amount => handleDecrement(breed, amount)"
    @reset="breed.count=0"
  />
  </div>

  <CounterSummary
    counterLabel="breeds"
    itemLabel="dogs"
    :data="dog_breeds"
    @resetAll="resetAllCounts"
  />
</template>

<style scoped>
.page-header {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  grid-column: 1 / -1;
  margin-bottom: 2rem;
}
:deep(.underline) {
  text-decoration: underline;
  text-decoration-color: #2c3e50;
  text-decoration-thickness: 2px;
  text-decoration-style: solid;
}
.breed-list {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  grid-column: 1 / -1;
}
.demo-container {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  grid-column: 1 / -1;
}
.container {
  display: flex;
  flex-direction: column;
  gap: 2rem;
  grid-column: 1 / -1;
  margin-bottom: 5rem;
}
</style>
