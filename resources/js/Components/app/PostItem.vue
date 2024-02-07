<script setup>
import { Disclosure, DisclosureButton, DisclosurePanel } from '@headlessui/vue'
  defineProps({
    post: Object
  });
  
</script>

<template>
  <div>
    <Disclosure v-slot="{ open }">
      <div v-if="!open" v-html="post.body.substring(0, 18)" />
      <DisclosurePanel>
        <div v-html="post.body" />
      </DisclosurePanel>
      <div class="flex justify-end">
        <DisclosureButton class="text-blue-500">
          {{ open ? 'Colapsar' : 'Mas' }}
          {{ console.log(post.body) }}
        </DisclosureButton>
      </div>
    </Disclosure>
  </div>
</template>

<style>
  
</style>