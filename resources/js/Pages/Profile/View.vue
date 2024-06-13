<template>
  <AuthenticatedLayout>
    <div class="w-[768px] mx-auto h-full overflow-auto">
      <div class="relative bg-white">
        <img src="https://www.prodraw.net/fb_cover/images/fb_cover_65.jpg" class="w-full h-[200px] object-cover">
        <div class="flex">
          <img src="https://cdn.iconscout.com/icon/free/png-256/free-avatar-370-456322.png?f=webp"
            class="ml-[48px] w-[128px] h-[128px] -mt-[64px]">
          <div class="flex justify-between items-center flex-1 p-4">
            <h2 class="font-bold text-lg">{{ user.name }}</h2>
            <PrimaryButton>
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                stroke="currentColor" class="w-4 h-4 mr-2">
                <path stroke-linecap="round" stroke-linejoin="round"
                  d="M16.862 4.487l1.687-1.688a1.875 1.875 0 112.652 2.652L6.832 19.82a4.5 4.5 0 01-1.897 1.13l-2.685.8.8-2.685a4.5 4.5 0 011.13-1.897L16.863 4.487zm0 0L19.5 7.125" />
              </svg>
              Editar Perfil
            </PrimaryButton>
          </div>
        </div>
      </div>
      <div class="border-t">
        <TabGroup>
          <TabList class="flex bg-white">
            <Tab v-slot="{ selected }" as="template">
              <TabItem text="Acerca De" :selected="selected" />
            </Tab>
            <Tab v-slot="{ selected }" as="template">
              <TabItem text="Posts" :selected="selected" />
            </Tab>
            <Tab v-slot="{ selected }" as="template">
              <TabItem text="Seguidores" :selected="selected" />
            </Tab>
            <Tab v-slot="{ selected }" as="template">
              <TabItem text="Siguiendo" :selected="selected" />
            </Tab>
            <Tab v-slot="{ selected }" as="template">
              <TabItem text="Fotos" :selected="selected" />
            </Tab>
          </TabList>

          <TabPanels class="mt-2">
            <TabPanel>
              <Edit :must-verify-email="mustVerifyEmail" :status="status" />
            </TabPanel>
            <TabPanel class="bg-white p-3 shadow">
              Posts
            </TabPanel>
            <TabPanel class="bg-white p-3 shadow">
              Seguidores
            </TabPanel>
            <TabPanel class="bg-white p-3 shadow">
              Siguiendo
            </TabPanel>
            <TabPanel class="bg-white p-3 shadow">
              Fotos
            </TabPanel>
          </TabPanels>

        </TabGroup>
      </div>
    </div>
  </AuthenticatedLayout>
</template>

<script setup>
import { computed, ref } from 'vue'
import { TabGroup, TabList, Tab, TabPanels, TabPanel } from '@headlessui/vue'
import { usePage } from '@inertiajs/vue3';
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import TabItem from "@/Pages/Profile/Partials/TabItem.vue";
import Edit from "@/Pages/Profile/Edit.vue";
import PrimaryButton from "@/Components/PrimaryButton.vue";

const user = usePage().props.auth.user;

const props = defineProps({
    mustVerifyEmail: {
        type: Boolean,
    },
    status: {
        type: String,
    },
    user: {
        type: Object
    }
});
</script>



<style scoped></style>