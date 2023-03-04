<script setup>
import { ref, onMounted, computed, watch} from 'vue'

const todos = ref([])
const name = ref('')



const input_content = ref('')
const input_category = ref(null)


const todos_asc = computed(() => todos.value.sort((a, b) => {
return b.createdAt - a.createdAt
}))








</script>

<template>
  <main class="app">

<section class="one">
  <h1 class="title">
Hello, <input type="text" placeholder="Insert Name" v-model="name">
  </h1>

</section>

  </main>


</template>