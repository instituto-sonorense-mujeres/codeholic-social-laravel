<script setup>
import TextInput from '../TextInput.vue';
import FollowingItem from './FollowingItem.vue';
  
</script>

<template>
  <div>
    <h2 class="text-2xl font-bold">Usuarios que sigues</h2>
    <TextInput/>

    <div class="py-8">
      <div v-if="false" class="text-grey-400 flex text-center">
        Aún no sigues a nadie
      </div>
      <div v-else>
        <FollowingItem 
          image="https://picsum.photos/100" 
          name="Joseph Smith"
         />
        <FollowingItem 
          image="https://picsum.photos/100" 
          name="Willy Wonca"
        />
      </div>
    </div>
    
  </div>
</template>

<style>
  
</style>