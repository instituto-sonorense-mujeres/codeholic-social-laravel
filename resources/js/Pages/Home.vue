<script setup>
import { Head, Link } from '@inertiajs/vue3';
import GroupItem from '@/Components/app/GroupItem.vue';

defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
    laravelVersion: {
        type: String,
        required: true,
    },
    phpVersion: {
        type: String,
        required: true,
    },
});
</script>

<template>
    
    <Head title="Codeholic Social Media" />

    <div class="grid grid-cols-12 gap-3">
        <div class="col-span-3 bg-sky-100 py-6 px-3">
            <h2 class="text-2xl font-bold">Mis Grupos</h2>

            <div class="py-8">
                <div v-if="false" class="text-grey-400 flex text-center">
                    No estas en ningun Grupo
                </div>
                
    
                <div v-else>
                    <GroupItem
                        image="https://picsum.photos/100"
                        title="Laravel Developers"
                        description="Lorem ipsum, dolor sit amet consectetur adipisicing elit. Optio quis recusandae iusto reprehenderit odit aspernatur, nobis atque eligendi vel laboriosam doloribus laborum omnis voluptate, repudiandae expedita earum consectetur temporibus perspiciatis"
                    /> 
                    <GroupItem
                        image="https://picsum.photos/100"
                        title="Vuejs Developers"
                        description="Lorem ipsum, dolor sit amet consectetur adipisicing elit. Optio quis recusandae iusto reprehenderit odit aspernatur, nobis atque eligendi vel laboriosam doloribus laborum omnis voluptate, repudiandae expedita earum consectetur temporibus perspiciatis"
                    />
                </div>
            </div>

        </div>
        <div class="col-span-6">
            Post
        </div>
        <div class="col-span-3">
            Followers
        </div>
    </div>


</template>

<style>
.bg-dots-darker {
    background-image: url("data:image/svg+xml,%3Csvg width='30' height='30' viewBox='0 0 30 30' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M1.22676 0C1.91374 0 2.45351 0.539773 2.45351 1.22676C2.45351 1.91374 1.91374 2.45351 1.22676 2.45351C0.539773 2.45351 0 1.91374 0 1.22676C0 0.539773 0.539773 0 1.22676 0Z' fill='rgba(0,0,0,0.07)'/%3E%3C/svg%3E");
}
@media (prefers-color-scheme: dark) {
    .dark\:bg-dots-lighter {
        background-image: url("data:image/svg+xml,%3Csvg width='30' height='30' viewBox='0 0 30 30' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M1.22676 0C1.91374 0 2.45351 0.539773 2.45351 1.22676C2.45351 1.91374 1.91374 2.45351 1.22676 2.45351C0.539773 2.45351 0 1.91374 0 1.22676C0 0.539773 0.539773 0 1.22676 0Z' fill='rgba(255,255,255,0.07)'/%3E%3C/svg%3E");
    }
}
</style>
