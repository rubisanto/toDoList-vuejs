<script setup lang="ts">
import {ref, onMounted, computed, watch} from 'vue'

const todos = ref([])
const name = ref('')

const input_content = ref('')
const input_category = ref(null)

const todos_asc = computed(() => todos.value.sort((a, b) =>{
  return b.createdAt - a.createdAt
 }
))

// surveiller les changements de la variable name
watch(name , (newVal) => {
  // enregistrer la valeur dans le localStorage
  localStorage.setItem('name', newVal)
})

onMounted(() => {
  // récupérer la valeur dans le localStorage
  name.value = localStorage.getItem('name') || ''
})
</script>

<template>
 <main class="app">
  <section class="greeting">
    <h2 class="title">
      What's up, <input type="text" placeholder="name here" v-model="name">
    </h2>
  </section>
  <section class="create-todo">
    <h3>CREATE A TODO</h3>
  </section>
 </main>
</template>

<style scoped>
</style>
