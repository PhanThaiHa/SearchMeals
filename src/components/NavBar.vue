<template>
    <header class="bg-white shadow h-16 flex justify-between items-stretch">
        <router-link :to="{ name: 'home' }"
            class="font-bold text-orange-400 inline-flex items-center hover:bg-orange-100 h-full px-5">
            Home
        </router-link>
        <div class="flex items-center gap-1">
            <router-link :to="{ name: 'byName' }"
                class="inline-flex items-center transition-colors px-2 h-full hover:bg-orange-400 hover:text-white">
                Search Meals
            </router-link>
            <router-link :to="{ name: 'byLetter' }"
                class="inline-flex items-center px-2 h-full hover:bg-orange-400 hover:text-white">
                Meals By Letters
            </router-link>
            <router-link :to="{ name: 'ingredients' }"
                class="inline-flex items-center px-2 h-full hover:bg-orange-400 hover:text-white">
                Meal By Ingredients
            </router-link>
        </div>
    </header>
</template>
