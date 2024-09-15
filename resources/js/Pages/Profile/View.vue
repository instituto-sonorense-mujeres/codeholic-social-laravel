<template>
  <AuthenticatedLayout>

    <div class="max-w-[768px] mx-auto min-h-screen overflow-auto">

      <div v-show="showNotification && status === 'cover-image-update'"
        class="my-2 py-2 px-3 font-medium text-sm bg-emerald-500 text-white">
        Your cover image has been updated
      </div>

      <div v-if="errors.cover" class="my-2 py-2 px-3 font-medium text-sm bg-red-400 text-white">
        {{ errors.cover }}
      </div>

      <div class="group relative bg-white">
        <img :src="coverImageSrc || user.cover_url || '/img/default.jpg'">
        <div class="absolute top-2 right-2 ">
          <button v-if="!coverImageSrc"
            class="bg-gray-50 hover:bg-gray-100 text-gray-800 py-1 px-2 text-xs flex items-center opacity-0 group-hover:opacity-100">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
              stroke="currentColor" class="w-3 h-3 mr-2">
              <path stroke-linecap="round" stroke-linejoin="round"
                d="M6.827 6.175A2.31 2.31 0 015.186 7.23c-.38.054-.757.112-1.134.175C2.999 7.58 2.25 8.507 2.25 9.574V18a2.25 2.25 0 002.25 2.25h15A2.25 2.25 0 0021.75 18V9.574c0-1.067-.75-1.994-1.802-2.169a47.865 47.865 0 00-1.134-.175 2.31 2.31 0 01-1.64-1.055l-.822-1.316a2.192 2.192 0 00-1.736-1.039 48.774 48.774 0 00-5.232 0 2.192 2.192 0 00-1.736 1.039l-.821 1.316z" />
              <path stroke-linecap="round" stroke-linejoin="round"
                d="M16.5 12.75a4.5 4.5 0 11-9 0 4.5 4.5 0 019 0zM18.75 10.5h.008v.008h-.008V10.5z" />
            </svg>

            actualizar imagen
            <input type="file" class="absolute left-0 top-0 bottom-0 right-0 opacity-0" @change="onCoverChange" />
          </button>

          <div v-else class="flex gap-2 bg-white p-2 opacity-0 group-hover:opacity-100">
            <button @click="cancelCoverImage"
              class="bg-gray-50 hover:bg-gray-100 text-gray-800 py-1 px-2 text-xs flex items-center">
              <XMarkIcon class="h-3 w-3 mr-2" />
              Cancel
            </button>
            <button @click="submitCoverImage"
              class="bg-gray-800 hover:bg-gray-900 text-gray-100 py-1 px-2 text-xs flex items-center">
              <CheckCircleIcon class="h-3 w-3 mr-2" />
              Submit
            </button>
          </div>
        </div>


        <div class="flex">
          <div
            class="flex items-center justify-center relative group/avatar -mt-[64px] ml-[48px] w-[128px] h-[128px] rounded-full">
            <img :src="avatarImageSrc || user.avatar_url || '/img/default_avatar.webp'"
              class="w-full h-full object-cover rounded-full">
            <button v-if="!avatarImageSrc"
              class="absolute left-0 top-0 right-0 bottom-0 bg-black/50 text-gray-200 rounded-full opacity-0 flex items-center justify-center group-hover/avatar:opacity-100">
              <CameraIcon class="w-8 h-8" />

              <input type="file" class="absolute left-0 top-0 bottom-0 right-0 opacity-0" @change="onAvatarChange" />
            </button>
            <div v-else class="absolute top-1 right-0 flex flex-col gap-2">
              <button @click="resetAvatarImage"
                class="w-7 h-7 flex items-center justify-center bg-red-500/80 text-white rounded-full">
                <XMarkIcon class="h-5 w-5" />
              </button>
              <button @click="submitAvatarImage"
                class="w-7 h-7 flex items-center justify-center bg-emerald-500/80 text-white rounded-full">
                <CheckCircleIcon class="h-5 w-5" />
              </button>
            </div>
          </div>
        </div>
      </div>
      <div class="border-t">
        <TabGroup>
          <TabList class="flex bg-white">
            <Tab v-if="isMyProfile" v-slot="{ selected }" as="template">
              <TabItem text="About" :selected="selected" />
            </Tab>
            <Tab v-slot="{ selected }" as="template">
              <TabItem text="Posts" :selected="selected" />
            </Tab>
            <Tab v-slot="{ selected }" as="template">
              <TabItem text="Followers" :selected="selected" />
            </Tab>
            <Tab v-slot="{ selected }" as="template">
              <TabItem text="Followings" :selected="selected" />
            </Tab>
            <Tab v-slot="{ selected }" as="template">
              <TabItem text="Photos" :selected="selected" />
            </Tab>
          </TabList>

          <TabPanels class="mt-2">
            <TabPanel v-if="isMyProfile">
              <Edit :must-verify-email="mustVerifyEmail" :status="status" />
            </TabPanel>
            <TabPanel class="bg-white p-3 shadow">
              Posts
            </TabPanel>
            <TabPanel class="bg-white p-3 shadow">
              Followers
            </TabPanel>
            <TabPanel class="bg-white p-3 shadow">
              Followings
            </TabPanel>
            <TabPanel class="bg-white p-3 shadow">
              Photos
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
import { XMarkIcon, CheckCircleIcon, CameraIcon } from '@heroicons/vue/24/solid';
import { useForm } from '@inertiajs/vue3'

const imagesForm = useForm({
  avatar: null,
  cover: null,
})

const showNotification = ref(true)

const authUser = usePage().props.auth.user;

const isMyProfile = computed(() => authUser && authUser.id == props.user.id);

const coverImageSrc = ref('');
const avatarImageSrc = ref('')

const props = defineProps({
  errors: Object,
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

const onCoverChange = (e) => {
  imagesForm.cover = e.target.files[0];
  if (imagesForm.cover) {
    const reader = new FileReader();
    reader.onload = () => {
      console.log("load happens");
      coverImageSrc.value = reader.result;
    }
    reader.readAsDataURL(imagesForm.cover);
  }
}


const onAvatarChange = (e) => {
  imagesForm.avatar = e.target.files[0];
  if (imagesForm.avatar) {
    const reader = new FileReader();
    reader.onload = () => {
      console.log("load happens");
      avatarImageSrc.value = reader.result;
    }
    reader.readAsDataURL(imagesForm.avatar);
  }
}

const cancelCoverImage = () => {
  imagesForm.cover = null;
  coverImageSrc.value = null;
}

const cancelAvatarImage = () => {
  imagesForm.avatar = null;
  avatarImageSrc.value = null;
}

const submitCoverImage = () => {
  console.log({"img":imagesForm.cover});
  imagesForm.post(route('profile.updateCover'), {
    onSuccess: (user) => {
      console.log({"usuario":user});
      cancelCoverImage();
      setTimeout( () => {
        showNotification.value = false;
      })
    }
  });
}

const submitAvatarImage = () => {
  console.log({"img":imagesForm.cover});
  imagesForm.post(route('profile.updateCover'), {
    onSuccess: (user) => {
      console.log({"usuario":user});
      cancelAvatarImage();
      setTimeout( () => {
        showNotification.value = false;
      })
    }
  });
}

</script>


<style scoped>

</style>