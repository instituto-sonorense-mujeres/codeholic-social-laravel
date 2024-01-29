<script setup>
  defineProps({
    image: String,
    title: String,
    description: String
  })

</script>

<template>
  <div class="flex items-start gap-3 mb-3 hover:bg-gray-100">
    <div class="flex items-start gap-3 py-2 px-3">

      <img :src="image" class="h-[48px] w-[48px] rounded-full" />
      <div>
        <h3 class="font-semibold">{{title}}</h3>
        <div class="text-sm text-gray-500">{{description}}</div>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>