<script setup>
import { Disclosure, DisclosureButton, DisclosurePanel } from '@headlessui/vue'
  defineProps({
    post: Object
  });
  
</script>

<template>
  <div>
    <Disclosure v-slot="{ open }">
      <DisclosureButton
        class="flex w-full justify-between rounded-lg bg-purple-100 px-4 py-2 text-left text-sm font-medium text-purple-900 hover:bg-purple-200 focus:outline-none focus-visible:ring focus-visible:ring-purple-500/75"
      >
        <span>What is your refund policy?</span>
        <ChevronUpIcon
          :class="open ? 'rotate-180 transform' : ''"
          class="h-5 w-5 text-purple-500"
        />
      </DisclosureButton>
      <DisclosurePanel class="px-4 pb-2 pt-4 text-sm text-gray-500">
        If you're unhappy with your purchase for any reason, email us within
        90 days and we'll refund you in full, no questions asked.
      </DisclosurePanel>
    </Disclosure>
    <div class="flex items-center gap-2 mb-3">
      <a href="javascript:void(0)">
        <img :src="post.user.avatar" class="w-[40px] rounded-full"/>
      </a>
    </div>
    <div>
      <h4 class="font-bold">
        <a href="javascript:void(0)">
          {{post.user.name}}
        </a>
      </h4>
      <small class="text-gray-400">{{post.created_at}}</small>
    </div>

    <div v-html="post.body"></div>
  </div>
</template>

<style>
  
</style>