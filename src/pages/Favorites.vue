<script setup>
import axios from 'axios'
import { inject, onMounted, ref } from 'vue'
import  CardList  from '../components/CardList.vue'

const favorites = ref([])

onMounted(async () => {
  try {
    const { data } = await axios.get(
      'https://c6106cae3d0d2840.mokky.dev/favorites?_relations=items'
    )

    favorites.value = data.map((obj) => obj.item)
  } catch {
    console.log('Error')
  }
})
</script>

<template>
  <h2 class="text-3xl font-bold mb-8">Мои избранные</h2>

  <CardList :items="favorites" is-favorites />
</template>
