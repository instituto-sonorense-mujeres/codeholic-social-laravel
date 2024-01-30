<script setup>
  defineProps({
    image: String,
    name: String,
  })

</script>

<template>
  <div class="mb-3 cursor-pointer hover:bg-gray-100">
    <div class="flex items-start gap-1 py-2 px-3">

      <img :src="image" class="h-[32px] w-[32px] rounded-full" />
      <div>
        <h3 class="font-semibold text-lg">{{name}}</h3>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>