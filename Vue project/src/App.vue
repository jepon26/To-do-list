<script setup>
import { ref, onMounted, computed, watch} from 'vue'

const todos = ref([])
const name = ref('')



const input_content = ref('')
const input_category = ref(null)


const todos_asc = computed(() => todos.value.sort((a, b) => {
return b.createdAt - a.createdAt
}))


watch(name, (newVal) => {
	localStorage.setItem('name', newVal)
})

watch(todos, (newVal) => {
  localStorage.setItem('todos', JSON.stringify(newVal))
}, {
  deep: true
})



const addTodo = () => {
  if(input_content.value.trim() === '' || input_category.value === nul) {
    return
  }



todos.value.push( {
  content: input_category.value,
  category: input_category.value,
  done: false,
  editable: false,
  createdAt: new Date().getTime()

})

}



const removeTodo = (todo) => {
  todos.value = todos.value.filter((t) => t !== todo)
}



onMounted(()=> {
  name.value =localStorage.getItem('name') || '' 
  todos.value = JSON.parse(localStorage.getItem('todos') || [])
})







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