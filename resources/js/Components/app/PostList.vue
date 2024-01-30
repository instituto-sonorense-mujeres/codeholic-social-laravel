<script setup>
import PostItem from './PostItem.vue';
const post1 = {
  user: {
    id: 1,
    avatar: 'https://randomuser.me/api/portraits/men/8.jpg',
    name: 'John Smith'
  },
  body: `
    <p>Lorem Ipsum</p>
  `,
  created_at: '2023-11-19 15:12'
}
  
</script>

<template>
  <div>
    <PostItem :post="post1"/>
    <PostItem :post="post1"/>
  </div>
</template>

<style>
  
</style>