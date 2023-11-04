<template>
  <VitePwaManifest />

  <div class="bg-black fixed w-[calc(100%+1px)] h-full"> 
    <NuxtPage />

    <CreatePost
      :class="[
          {'max-h-[100vh] transition-all duration-200 ease-in visible': userStore.isMenuOverlay },
          {'max-h-0 transition-all duration-200 ease-out invisible': !userStore.isMenuOverlay },
      ]"
    />

    <Modal 
      :class="[
          {'max-h-[100vh] transition-all duration-200 ease-in visible': userStore.isLogoutOverlay },
          {'max-h-0 transition-all duration-200 ease-out invisible': !userStore.isLogoutOverlay },
      ]"
    />
  </div>
</template>

<script setup>
import { useUserStore } from '~/stores/user';

useSeoMeta({
  title: 'Threads PWA Clone',
  ogTitle: 'Threads PWA Clone',
  description: 'This is a PWA practice similar to Threads app, you can test some of the functions like create a new post. Have fun testing it.',
  ogDescription: 'This is a PWA practice similar to Threads app, you can test some of the functions like create a new post. Have fun testing it.',
  ogImage: './public/meta-picture.png',
  twitterCard: 'summary_large_image',
})

const userStore = useUserStore()
</script>
