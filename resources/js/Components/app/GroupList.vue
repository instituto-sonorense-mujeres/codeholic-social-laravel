<script setup>

import GroupItem from '@/Components/app/GroupItem.vue';
import TextInput from '../TextInput.vue';

</script>

<template>
  <div>
    <h2 class="text-2xl font-bold">Mis Grupos</h2>

    <TextInput/>

    <div class="py-8">
      <div v-if="false" class="text-grey-400 flex text-center">
        No estas en ningun Grupo
      </div>


      <div v-else>
        <GroupItem image="https://picsum.photos/100" title="Laravel Developers"
          description="Lorem ipsum, dolor sit amet consectetur adipisicing elit. Optio quis recusandae iusto reprehenderit odit aspernatur, nobis atque eligendi vel laboriosam doloribus laborum omnis voluptate, repudiandae expedita earum consectetur temporibus perspiciatis" />
        <GroupItem image="https://picsum.photos/100" title="Vuejs Developers"
          description="Lorem ipsum, dolor sit amet consectetur adipisicing elit. Optio quis recusandae iusto reprehenderit odit aspernatur, nobis atque eligendi vel laboriosam doloribus laborum omnis voluptate, repudiandae expedita earum consectetur temporibus perspiciatis" />
      </div>
    </div>

  </div>
</template>

<style></style>