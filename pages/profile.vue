<template>
    <MainLayout>
    <div id="ProfilePage" class="w-full">
        <div v-if="user" class="mx-auto max-w-[500px] overflow-hidden mt-6">
            
                <div  class="flex items-center text-white">
                    <div class="flex items-center justify-between text-white w-full">
                        <div class="ml-2 font-semibold text-[18px]">{{ user.identities[0].identity_data.full_name }}</div>
                        <img class="rounded-full h-[35px]" :src="user.identities[0].identity_data.avatar_url">
                    </div>
                </div>
            <div class="flex flex-col items-center justify-around h-full border border-gray-600 rounded-lg mt-8">
                <div class="flex items-center justify-center text-white font-semibold h-20 mt-4">
                    <p>Welcome back! enjoy this funny app</p>
                </div>
                <div class="w-full">
                    <div 
                        class="h-60 flex flex items-center justify-center text-white"
                    >
                    <button 
                            @click="userStore.isLogoutOverlay = true"
                            class="
                            flex 
                            items-center 
                            justify-center 
                            gap-3
                            p-1.5
                            w-1/2
                            border 
                            rounded-full
                            text-lg
                            font-semibold
                            "
                        >
                        Log out <Icon class="mb-1" name="ph:sign-out" size="28" color="#ffffff"/>
                        </button>
                    </div>
                </div>    
            </div>
        </div>

        <div v-else class="flex justify-center h-60 mx-auto max-w-[500px] overflow-hidden mt-20 border border-gray-600 rounded-lg">
            <div class="flex flex-col items-center justify-around h-full">
            <div class="flex items-center justify-center text-white w-4/5">
                <p>You need to login or register to play and test this clone app. Have fun!</p>
            </div>
            <button 
                    @click="navigateTo('/auth')"
                    class="
                        flex 
                        items-center 
                        justify-center 
                        gap-3
                        p-1.5
                        w-1/2
                        border 
                        rounded-full
                        text-lg
                        font-semibold
                    "
                >
                    <div class="flex items-center text-white gap-2 justify-center">
                        Login / Register
                    </div>
                </button>
            </div>
        </div>
    </div>
</MainLayout>        
</template>

<script setup>
import MainLayout from '~/layouts/MainLayout.vue';
import { useUserStore } from '~/stores/user';
const userStore = useUserStore()
const client = useSupabaseClient()
const user = useSupabaseUser()
</script>