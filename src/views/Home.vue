<template>
    <div class="flex flex-col p-8">
        <div>
            <h2 class="text-4xl font-bold text-orange-400">Random Meals</h2>
        </div>
    </div>
    <Meals :meals="meals" />
</template> 

<script setup>
import { computed, onMounted, ref } from 'vue';
import store from '../store';
import axiosClient from '../axiosClient.js'
import Meals from '../components/Meals.vue';

const meals = ref([]);

onMounted(async () => {
    for (var i = 0; i < 9; i++) {
        axiosClient.get('random.php').then(({ data }) => {
            meals.value.push(data.meals[0]);
        });
    }
})
</script>