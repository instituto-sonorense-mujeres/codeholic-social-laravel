<script setup>
import TextInput from "@/Components/TextInput.vue";
import FollowingItem from "@/Components/app/FollowingItem.vue";
import {ref} from "vue";

const searchKeyword = ref('')

</script>

<template>
    <TextInput :model-value="searchKeyword" placeholder="Type to search" class="border-gray-300 dark:border-gray-700 dark:bg-gray-900 dark:text-gray-300 focus:border-indigo-500 dark:focus:border-indigo-600 focus:ring-indigo-500 dark:focus:ring-indigo-600 rounded-md shadow-sm"/>
    <div class="mt-3 h-[200px] lg:flex-1 overflow-auto">
        <div v-if="false" class="text-gray-400 text-center p-3">
            Aun no sigues a nadie
        </div>
        <div v-else>
            <FollowingItem image="https://picsum.photos/100"
                           title="John Doe"
                           description="Lorem ipsum dolor sit amet, consectetur adipisicing elit."/>
            <FollowingItem image="https://picsum.photos/100"
                           title="Elon Musk"
                           description="Lorem ipsum dolor sit amet, consectetur adipisicing elit."/>
            <FollowingItem image="https://picsum.photos/100"
                           title="John Doe"
                           description="Lorem ipsum dolor sit amet, consectetur adipisicing elit."/>
            <FollowingItem image="https://picsum.photos/100"
                           title="Elon Musk"
                           description="Lorem ipsum dolor sit amet, consectetur adipisicing elit."/>
            <FollowingItem image="https://picsum.photos/100"
                           title="John Doe"
                           description="Lorem ipsum dolor sit amet, consectetur adipisicing elit."/>
            <FollowingItem image="https://picsum.photos/100"
                           title="Elon Musk"
                           description="Lorem ipsum dolor sit amet, consectetur adipisicing elit."/>
            <FollowingItem image="https://picsum.photos/100"
                           title="John Doe"
                           description="Lorem ipsum dolor sit amet, consectetur adipisicing elit."/>
            <FollowingItem image="https://picsum.photos/100"
                           title="Elon Musk"
                           description="Lorem ipsum dolor sit amet, consectetur adipisicing elit."/>
            <FollowingItem image="https://picsum.photos/100"
                           title="John Doe"
                           description="Lorem ipsum dolor sit amet, consectetur adipisicing elit."/>
            <FollowingItem image="https://picsum.photos/100"
                           title="Elon Musk"
                           description="Lorem ipsum dolor sit amet, consectetur adipisicing elit."/>
            <FollowingItem image="https://picsum.photos/100"
                           title="John Doe"
                           description="Lorem ipsum dolor sit amet, consectetur adipisicing elit."/>
            <FollowingItem image="https://picsum.photos/100"
                           title="Elon Musk"
                           description="Lorem ipsum dolor sit amet, consectetur adipisicing elit."/>
            <FollowingItem image="https://picsum.photos/100"
                           title="John Doe"
                           description="Lorem ipsum dolor sit amet, consectetur adipisicing elit."/>
            <FollowingItem image="https://picsum.photos/100"
                           title="Elon Musk"
                           description="Lorem ipsum dolor sit amet, consectetur adipisicing elit."/>
        </div>
    </div>
</template>

<style scoped>

</style>