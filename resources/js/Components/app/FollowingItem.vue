<script setup>
defineProps({
    image: String,
    title: String,
})
</script>

<template>
    <div class="mb-3 cursor-pointer hover:bg-zinc-950">
        <div class="flex items-center gap-2 py-2 px-2">
            <img :src="image" class="w-[32px] rounded-full"/>
            <div>
                <h3 class="border-gray-300 dark:border-gray-700 dark:bg-gray-900 dark:text-gray-300 focus:border-indigo-500 dark:focus:border-indigo-600 focus:ring-indigo-500 dark:focus:ring-indigo-600 rounded-md shadow-sm">{{ title }}</h3>
            </div>
        </div>
    </div>
</template>

<style scoped>

</style>