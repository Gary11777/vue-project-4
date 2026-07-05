<script setup>
import { ref, reactive, computed } from 'vue'

const isActive = ref(true)
const isError = ref(false)
const error = ref(null)

const activeClass = 'active'
const errorClass = 'text-danger'

const activeColor = ref('red')
const fontSize = ref('30')

// const classObject = reactive({
//   active: true,
//   'text-danger': true
// })
const classObject = computed(() => ({
  active: isActive.value && !error.value,
  'text-danger': error.value && error.value.type === 'fatal'
}))

const styleObject = computed(() => ({
  color: activeColor.value,
  fontSize: fontSize.value + 'px'
}))
</script>

<template>
<header class="page-header">
    <h1>Class and Style Bindings</h1>
    <div 
    class="static-class"
    :class="{ active: isActive, 'text-danger': isError }"
    >
    Some texte with a class binding
    </div>
    <div :style="{ color: isError ? 'red' : 'green', fontSize: '1.5rem' }">
        Some texte with a style binding
    </div>
    <div :class="classObject">
        Some texte with a style object binding
    </div>
    <div :class="[activeClass, errorClass]">
        Some texte with a class array binding 1
    </div>
    <div :class="[isActive ? activeClass : '', isError ? errorClass : '']">
        Some texte with a class array binding 2
    </div>
    <div :class="[{ [activeClass]: isActive },  errorClass]">
        Some texte with a class array binding 2
    </div>
    <div :style="{ color: activeColor, fontSize: fontSize + 'px' }">
        Some texte with a style binding
    </div>
    <div :style="styleObject">
        Some texte with a style object binding
    </div>
</header>
</template>

<style scoped>
.static-class {
  font-weight: bold;
}
.active {
  background-color: #f0f0f0;
  padding: 1rem;
  border-radius: 0.5rem;
}
.text-danger {
  color: red;
}
</style>