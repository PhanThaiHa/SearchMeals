<template>
    <div class="p-8 pb-0">
        <p class="px-8 text-4xl text-orange-400 font-bold mb-4">Search Meals by Name</p>
        <div class="px-8 mt-7">
            <input type="text" v-model="keyword"
                class="rounded border-2 bg-white border-gray-200 w-full focus:border-orange-500 focus:ring-orange-500"
                placeholder="Search for meals..." @change="searchMeals" />
        </div>
    </div>
    <Meals :meals="meals" />
</template>

<script setup>
import { onMounted, ref } from 'vue';
import store from '../store';
import { computed } from '@vue/reactivity';
import { useRoute } from 'vue-router';
import Meals from '../components/Meals.vue';

const route = useRoute();
var keyword = ref("");
const meals = computed(() => store.state.searchedMeals);

function searchMeals() {
    if (keyword.value) {
        store.dispatch('searchMeals', keyword.value);
    } else {
        store.commit('setSearchMeals', []);
    }

}

onMounted(() => {
    keyword.value = route.params.name;
    if (keyword.value) {
        searchMeals();
    }
})



</script>