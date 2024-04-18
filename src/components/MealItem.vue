<template>
    <div :key="key" class="bg-white shadow rounded-xl hover:scale-105 transition-all">
        <router-link :to="{ name: 'mealDetails', params: { id: meal.idMeal } }">
            <img :src="meal.strMealThumb" :alt="meal.strMeal" class="rounded-t-xl h-48 w-full object-cover">
        </router-link>
        <div class="p-3">
            <h3 class="font-bold">{{ meal.strMeal }}</h3>
            <p class="mb-4">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum auctor aliquam odio,
                eget commodo
                nisi molestie sed</p>
            <YouTubeButton class="my-2" :href="meal.strYoutube">Youtube</YouTubeButton>
        </div>
    </div>
</template>

<script setup>
import YouTubeButton from './YouTubeButton.vue';

const { meal } = defineProps({
    meal: {
        required: true,
        type: Object
    }
})
</script>