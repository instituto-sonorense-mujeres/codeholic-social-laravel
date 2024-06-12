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
            <PrimaryButton v-if="isMyProfile">
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
          <TabList class="flex space-x-1 rounded-xl bg-blue-900/20 p-1">
            <Tab v-for="category in Object.keys(categories)" as="template" :key="category" v-slot="{ selected }">
              <button :class="[
                'w-full rounded-lg py-2.5 text-sm font-medium leading-5',
                'ring-white/60 ring-offset-2 ring-offset-blue-400 focus:outline-none focus:ring-2',
                selected
                  ? 'bg-white text-blue-700 shadow'
                  : 'text-blue-100 hover:bg-white/[0.12] hover:text-white',
              ]">
                {{ category }}
              </button>
            </Tab>
          </TabList>

          <TabPanels class="mt-2">
            <TabPanel v-for="(posts, idx) in Object.values(categories)" :key="idx" :class="[
              'rounded-xl bg-white p-3',
              'ring-white/60 ring-offset-2 ring-offset-blue-400 focus:outline-none focus:ring-2',
            ]">
              <ul>
                <li v-for="post in posts" :key="post.id" class="relative rounded-md p-3 hover:bg-gray-100">
                  <h3 class="text-sm font-medium leading-5">
                    {{ post.title }}
                  </h3>

                  <ul class="mt-1 flex space-x-1 text-xs font-normal leading-4 text-gray-500">
                    <li>{{ post.date }}</li>
                    <li>&middot;</li>
                    <li>{{ post.commentCount }} comments</li>
                    <li>&middot;</li>
                    <li>{{ post.shareCount }} shares</li>
                  </ul>

                  <a href="#" :class="[
                    'absolute inset-0 rounded-md',
                    'ring-blue-400 focus:z-10 focus:outline-none focus:ring-2',
                  ]" />
                </li>
              </ul>
            </TabPanel>
          </TabPanels>
        </TabGroup>
      </div>
    </div>
  </AuthenticatedLayout>
</template>

<script setup>
import { ref } from 'vue'
import { TabGroup, TabList, Tab, TabPanels, TabPanel } from '@headlessui/vue'
import { usePage } from '@inertiajs/vue3';
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';


const user = usePage().props.auth.user;

const categories = ref({
  Recent: [
    {
      id: 1,
      title: 'Does drinking coffee make you smarter?',
      date: '5h ago',
      commentCount: 5,
      shareCount: 2,
    },
    {
      id: 2,
      title: "So you've bought coffee... now what?",
      date: '2h ago',
      commentCount: 3,
      shareCount: 2,
    },
  ],
  Popular: [
    {
      id: 1,
      title: 'Is tech making coffee better or worse?',
      date: 'Jan 7',
      commentCount: 29,
      shareCount: 16,
    },
    {
      id: 2,
      title: 'The most innovative things happening in coffee',
      date: 'Mar 19',
      commentCount: 24,
      shareCount: 12,
    },
  ],
  Trending: [
    {
      id: 1,
      title: 'Ask Me Anything: 10 answers to your questions about coffee',
      date: '2d ago',
      commentCount: 9,
      shareCount: 5,
    },
    {
      id: 2,
      title: "The worst advice we've ever heard about coffee",
      date: '4d ago',
      commentCount: 1,
      shareCount: 2,
    },
  ],
})
</script>



<style scoped></style>