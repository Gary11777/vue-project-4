<script setup lang="ts">

//PROPS
/*
defineProps({
  count: {
    type: Number,
    required: true
  },
  label: {
    type: String,
    required: true
  },
  disabled: {
    type: Boolean,
    default: false
  }
})
*/
interface CounterProps {
  count: number,
  label: string,
  disabled?: boolean
}

defineProps<CounterProps>()


//EMITS
//defineEmits(['increment', 'decrement', 'reset'])
defineEmits<{
  'increment': [number],
  'decrement': [number],
  'reset': []
}>()

</script>

<template>
  <section class="counter" :class="{ disabled: disabled }">
    <button @click="$emit('increment', 1)">+</button>
    <button @click="$emit('decrement', 1)">-</button>
    <h2>{{count}} {{label}}{{count !==1 ? 's' : ''}}</h2>
    <button class="reset" @click="$emit('reset')">Reset</button>
  </section>
</template>

<style scoped>
  .counter{
    display:flex;
    align-items:center;
    gap:10px;
  }

  .counter button{
    font-size:1.2rem;
    cursor:pointer;
    opacity:0.5;
    background: none;
    border: 0;
    color: gray;
    transition: opacity 0.3s;
  }
  .counter button:hover{
    opacity:1;
  }

  button.reset{
    font-size:0.9rem;
  }
  .disabled {
  pointer-events: none;
  opacity: 0.5;
  user-select: none;
  text-decoration: line-through;
}
</style>