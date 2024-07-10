<script setup>
import CardList from '../components/CardList.vue'
import { ref, onMounted } from 'vue'
import axios from 'axios'

const favorites = ref([])

onMounted(async () => {
    try {
        const { data } = await axios.get('https://2b7b7a394d07ad8b.mokky.dev/favorites?_relations=items')
        favorites.value = data.map(obj => obj.item)
    } catch (error) {
        console.error('Error fetching favorites:', error)
    }
})


</script>

<template>
    <h2 class="text-3xl font-bold mb-8">Мои закладки</h2>

    <CardList :items="favorites" is-favorites />
</template>