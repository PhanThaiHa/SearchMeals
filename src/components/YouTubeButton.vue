<template>
    <div>
        <a :href="href" target="_blank"
            class="px-3 py-2 rounded border-2 border-orange-400 hover:border-orange-700 bg-orange-400 text-white hover:bg-orange-700 transition-colors">
            <slot></slot>
        </a>
    </div>
</template>

<script setup>
const props = defineProps({
    href: String
})
</script>
