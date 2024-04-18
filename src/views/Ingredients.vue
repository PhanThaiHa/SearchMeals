<template>
    <div class="p-8">
        <h1 class="px-8 text-4xl mb-4 font-bold text-orange-400">Ingredients</h1>
        <div class="px-8 mt-7">
            <input type="text" v-model="keyword"
                class="rounded border-2 bg-white border-gray-200 w-full mb-4 focus:border-orange-400 focus:ring-orange-400"
                placeholder="Search for ingredients..." @change="searchIngredient" />
        </div>
        <router-link :to="{ name: 'byIngredient', params: { ingredient: ingredient.strIngredient } }"
            v-for="ingredient of computedIngredients" :key="ingredient.idIngredient"
            class="block bg-white rounded p-6 mb-4 shadow hover:bg-orange-50">
            <h3 class="text-2xl font-bold mb-2">{{ ingredient.strIngredient }}</h3>
            <p>{{ ingredient.strDescription }}</p>
        </router-link>
    </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';
import axiosClient from '../axiosClient';
import { computed } from '@vue/reactivity';
const computedIngredients = computed(() => {
    if (keyword.length != 0) {
        return ingredients.value.filter((i) => i.strIngredient.toLowerCase().includes(keyword.value.toLowerCase()));
    }
})

const keyword = ref("");
const ingredients = ref([]);

onMounted(() => {
    axiosClient.get("list.php?i=list")
        .then(({ data }) => {
            ingredients.value = data.meals
        })
})
</script>