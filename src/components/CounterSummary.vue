<script setup lang="ts">
import {computed} from 'vue'

//PROPS
// const props = defineProps({
//   counterLabel: {
//     type: String,
//     required: true
//   },
//   itemLabel: {
//     type: String,
//     required: true
//   },
//   data: {
//     type: Array,
//     required: true
//   }
// })
interface CounterSummaryProps {
  counterLabel: string,
  itemLabel: string,
  data: Array<{
    label: string,
    count: number,
    disabled?: boolean
  }>
}
const props = defineProps<CounterSummaryProps>()

//EMITS
//defineEmits(['resetAll'])
defineEmits<{
  'resetAll': []
}>()

//COMPUTED

//Calculate total dogs counted
const totalCount = computed(() =>
  props.data.reduce((sum, breed) => {
    return breed.disabled ? sum : sum + Number(breed.count)
  }, 0)
)

//calculate total breeds counted
const totalBreeds = computed(() =>
  props.data.filter(breed =>
    !breed.disabled && Number(breed.count) > 0
  ).length
)

</script>

<template>
  <section id="summary">
    <p>Total {{counterLabel}}: {{totalBreeds}}</p>
    <p>Total {{itemLabel}}: {{totalCount}}</p>
    <button @click="$emit('resetAll')">Reset all</button>
  </section>
</template>

<style scoped>
#summary{
  font-size:1.2rem;
  margin-top:10px;
}
button{
  cursor:pointer;
  opacity:0.5;
  background: none;
  border: 0;
  color: gray;
  transition: opacity 0.3s;
  font-size:0.9rem;
}
button:hover{
  opacity:1;
}
</style>