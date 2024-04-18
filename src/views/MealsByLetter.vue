<template>
    <div class="p-8 pb-0">
        <h1 class=" px-8 text-4xl font-bold mb-4 text-orange-400">Search Meals by Letter</h1>
    </div>
    <div class="flex flex-wrap justify-center my-3 gap-3 text-gray-700 px-8">
        <router-link :to="{ name: 'byLetter', params: { letter } }" v-for="letter of letters" :key="letter"
            class="h-2 hover:scale-150 items-center justify-center transition-all hover:text-orange-400">
            {{ letter }}
        </router-link>
    </div>
    <Meals :meals="meals" />
</template>

<script setup>
import { computed } from '@vue/reactivity';
import { onMounted, watch } from 'vue';
import store from '../store';
import { useRoute } from 'vue-router';
import Meals from '../components/Meals.vue';

const route = useRoute();
const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split("");
const meals = computed(() => store.state.mealsByLetter);

watch(route, () => {
    store.dispatch('searchMealsByLetter', route.params.letter);
})

onMounted(() => {
    store.dispatch('searchMealsByLetter', route.params.letter);
})
</script>