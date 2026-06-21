<script setup>
import Counter from '@/components/Counter.vue'
import CounterSummary from '@/components/CounterSummary.vue'
import {ref} from 'vue'

//Data
const dog_breeds = ref([
{label: 'Dalmatian', count: 0},
{label: 'Pug', count: 0},
{label: 'Beagle', count: 0, disabled: true},
{label: 'Poodle', count: 0},
{label: 'Bulldog', count: 0, disabled: true},
])

//HANDLERS
//Increase count for breed
const handleIncrement = (breed, amount) => {
  breed.count += amount
}

//Decrease count for breed
const handleDecrement = (breed, amount) => {
  if (breed.count - amount >= 0) breed.count -= amount
}

//Reset all counts
const resetAllCounts = () => {
  dog_breeds.value.forEach(breed => {
    breed.count = 0
  })
}

</script>

<template>
  <h1>Dog Park Counter</h1>

  <div class="breed-list">
  <Counter 
    v-for="breed in dog_breeds" 
    :label="breed.label" 
    :count="breed.count"
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
.breed-list {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  grid-column: 1 / -1; /* spans full width inside the 2-column #app grid */
}
</style>