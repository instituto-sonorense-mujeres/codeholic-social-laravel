<script setup>
import PostItem from './PostItem.vue';
const post1 = {
  user: {
    id: 1,
    avatar: 'https://randomuser.me/api/portraits/men/8.jpg',
    name: 'John Smith'
  },
  body: `
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Alias aspernatur aut, consequatur cum cupiditate dicta dolores dolorum facere fugit harum labore minima necessitatibus nobis pariatur provident, quia sequi sint voluptatibus.</p>
  `,
  group: null,
  attachments: [
        {
            id: 1,
            name: 'test.png',
            url: 'https://picsum.photos/1000',
            mime: 'image/png'
        },
        {
            id: 2,
            name: 'test2.png',
            url: 'https://picsum.photos/1000',
            mime: 'image/png'
        },
        {
            id: 3,
            name: 'MyDocument.docx',
            url: '#',
            mime: 'application/msword'
        }
    ],
  created_at: '2023-11-19 15:12'
}
const post2 = {
  user: {
    id: 2,
    avatar: 'https://randomuser.me/api/portraits/men/9.jpg',
    name: 'Joseph Smith'
  },
  group: {
    id: 1,
    name: 'Laravel Developers'
  },
  body: `
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Alias aspernatur aut, consequatur cum cupiditate dicta dolores dolorum facere fugit harum labore minima necessitatibus nobis pariatur provident, quia sequi sint voluptatibus.</p>
  `,
  created_at: '2023-11-19 15:12'
}
  
</script>

<template>
  <div class="overflow-auto">
    <PostItem :post="post1"/>
    <PostItem :post="post2"/>
  </div>
</template>

<style>
  
</style>