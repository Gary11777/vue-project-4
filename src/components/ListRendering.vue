<script setup>
import { ref, reactive, computed } from 'vue'

const adminUsers = computed(() =>
  ListOfUsers.value.filter(user => !user.isAdmin)
)

const parentMessage = ref('Parent')
const items = ref([
    { message: 'Foo', id: 1 },
    { message: 'Bar', id: 2 },
    { message: 'Baz', id: 3 }
])
const myObject = reactive({
  title: 'How to do lists in Vue',
  author: 'Jane Doe',
  publishedAt: '2016-04-10'
})
const books = ref([
  { title: 'Vue 3 Guide', author: 'Jane Doe', publishedAt: '2016-04-10' },
  { title: 'Vue 3 Guide', author: 'Ihar Ushakou', publishedAt: '2026-07-19' },
  { title: 'Vue 3 Guide', author: 'Elon Musk', publishedAt: '2026-07-18' }
])
const ListOfUsers = ref([
  {
    name: 'Ihar Ushakou',
    details: {
      firstname: 'Ihar',
      lastname: 'Ushakou',
      dateofbirth: '09-03-1984',
    },
    isAdmin: true
  },
  {
    name: 'Jane Doe',
    details: {
      firstname: 'Jane',
      lastname: 'Doe',
      dateofbirth: '10-04-1990',
    },
    isAdmin: false
  },
  {
    name: 'Jim Doe',
    details: {
      firstname: 'Jim',
      lastname: 'Doe',
      dateofbirth: '11-05-1995',
    },
    isAdmin: false
  }
])
</script>

<template>

    <section class="container">
        <header class="page-header">
            <h1 class="underline">List Rendering</h1>
        </header>

        <div class="demo-container">
            <ul>
                <li v-for="(item, index) in items">
                    {{ parentMessage }} - {{ index }} - {{  item.message }} - {{ item.id }}
                </li>
            </ul>
            <ul>
                <li v-for="value in myObject">
                    {{ value }}
                </li>
            </ul>
            <ul>
                <li v-for="book in books">
                    {{ book.title }} - {{ book.author }} - {{ book.publishedAt }}
                </li>
            </ul>
            <ul>
                <li v-for="user in adminUsers">
                        {{ user.name }}:
                        <ul>
                            <li>
                                First name: {{ user.details.firstname }}
                            </li>
                            <li>
                                Last name: {{ user.details.lastname }}
                            </li>
                            <li>
                                Date of birth: {{ user.details.dateofbirth }}
                            </li>
                        </ul>
                </li>
            </ul>
            <span v-for="n in 10">
                {{ n }}
            </span>
        </div>
    </section>

</template>