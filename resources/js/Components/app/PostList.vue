<script setup>
import PostItem from './PostItem.vue';
const post1 = {
  user: {
    id: 1,
    avatar: 'https://randomuser.me/api/portraits/men/8.jpg',
    name: 'John Smith'
  },
  body: `
    <p>John Smith says something</p>
  `,
  created_at: '2023-11-19 15:12'
}
const post2 = {
  user: {
    id: 2,
    avatar: 'https://randomuser.me/api/portraits/men/9.jpg',
    name: 'Joseph Smith'
  },
  body: `
    <p>Joseph Smith says something</p>
  `,
  created_at: '2023-11-19 15:12'
}
  
</script>

<template>
  <div>
    <PostItem :post="post1"/>
    <PostItem :post="post2"/>
  </div>
</template>

<style>
  
</style>