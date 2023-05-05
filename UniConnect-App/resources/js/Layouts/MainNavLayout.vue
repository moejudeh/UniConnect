<script setup>

import { ref } from 'vue';
import { Link, usePage} from '@inertiajs/vue3';
import Home from 'vue-material-design-icons/Home.vue'
import Magnify from 'vue-material-design-icons/Magnify.vue' 
import HomeOutline from 'vue-material-design-icons/HomeOutline.vue'
import Chat from 'vue-material-design-icons/Chat.vue'
import AccountGroup from 'vue-material-design-icons/AccountGroup.vue'
import DotsGrid from 'vue-material-design-icons/DotsGrid.vue'
import Bell from 'vue-material-design-icons/Bell.vue'
import Logout from 'vue-material-design-icons/Logout.vue'
import Contacts from 'vue-material-design-icons/Contacts.vue'

import CropperModal from '@/Components/CropperModal.vue'
import ImageDisplay from '@/Components/ImageDisplay.vue'
import CreatePostOverlay from '@/Components/CreatePostOverlay.vue';
import { useGeneralStore } from '@/stores/general';
import { storeToRefs } from 'pinia';
const useGeneral = useGeneralStore()
const { isPostOverlay, isCropperModal, isImageDisplay } = storeToRefs(useGeneral)

const user = usePage().props.auth.user

let showMenu = ref(false)
</script>

<template>
    <div 
        id="MainNav"
        class = "fixed z-50 w-full flex items-center justify-evenly h-[80px] bg-white shadow-xl border-b"
    >
        <div id = "NavLeft" class = "flex items-center justify-start w-[280px]">
            <Link href="/" class ="pl-3 min-w[56px]">
                <img class = "mb-[5px]  h-[45px] w-[70px]" src="../../../public/img/UniConnect-purple-cap.png"/>
            </Link>
            <div class="flex items-center justify-center bg-[#EFF2F5] p-1 rounded-full h-[40px] ml-2">
                <Magnify class="p-1" :size="22" fillColor="#64676B"/>
                <input
                    class="
                        lg:block
                        hidden
                        border-none
                        p-0
                        bg-[#EFF2F5]
                        placeholder-[#64676B]
                        ring-0
                        focus:ring-0
                    "
                    placeholder="Search UniConnect"
                    type="text"
                >
            </div>
        </div>
        <div id="NavCenter" class=" hidden lg:flex items-center ml-5 justify-center w-8/12 max-w-[600px]">
            <Link href="/" class ="w-full">
                <div 
                :class="$page.url === '/' ? 'mt-1.5' : '' "
                class = "flex items-center justify-center h-[48px] p-1 hover:bg-[#F2F2F2] w-full rounded-lg cursor-pointer transition-[.8s]"
                >
                    <div>
                        <Home v-if="$page.url === '/'" class ="mx-auto" :size="27" fillColor = "#5800AE"/>
                        <HomeOutline v-else class ="mx-auto" :size="27" fillColor = "#64676B"/>
                    </div>
                </div>
                <div 
                    v-if="$page.url === '/'"
                    class ="border-b-4 border-b-purple-400 rounded-md"
                ></div>
            </Link>
            <Link href="/clubs" class ="w-full">
            <button class = "flex items-center justify-center h-[48px] p-1 hover:bg-[#F2F2F2] w-full rounded-lg mx-1 cursor-pointer transition-[.8s]">
                    <AccountGroup  v-if="$page.url === '/clubs'" class ="mx-auto" :size="27" fillColor="#5800AE"/>
                    <AccountGroup v-else class ="mx-auto" :size="27" fillColor = "#64676B"/>      
            </button>
            <div 
                    v-if="$page.url === '/clubs'"
                    class ="border-b-4 border-b-purple-400 rounded-md"
            ></div>
            </Link>
            <button class = "flex items-center justify-center h-[48px] p-1 hover:bg-[#F2F2F2] w-full rounded-lg mx-1 cursor-pointer transition-[.8s]">
                <Chat class ="mx-auto" :size="25" fillColor="#64676B"/>    
            </button>
            <button class = "flex items-center justify-center h-[48px] p-1 hover:bg-[#F2F2F2] w-full rounded-lg mx-1 cursor-pointer transition-[.8s]" >
                <Contacts class ="mx-auto" :size="25" fillColor="#64676B"/>    
            </button>
        </div>
        <div class ="flex items-center justify-end w-2/12 mr-4">
            <button class="rounded-full bg-[#E3E6EA] p-2 hover:bg-purple-600 mx-1 cursor-pointer transition-[.8s]">
                <Bell :size="23" fillColor="#050505"/>
            </button>
            <button class="rounded-full bg-[#E3E6EA] p-2 hover:bg-purple-600 mx-1 cursor-pointer transition-[.8s]">
                <DotsGrid :size="23" fillColor="#050505"/>
            </button>
            <div class="flex items-center justify-center relative">
                <button @click="showMenu = !showMenu">
                    <img 
                        class="rounded-full ml-1 min-w-w[40px] max-h-[40px] cursor-pointer" 
                        :src="user.image"
                        />
                </button>
                <div 
                    v-if="showMenu"
                    class="absolute bg-white shadow-xl top-10 right-0 w-[330px] rounded-lg p-1 border mt-1">
                    <Link :href="route('user.show',{id: user.id})" @click="showMenu = !showMenu">
                        <div class="flex items-center gap-3 hover:bg-gray-200 p-2 rounded-lg">
                            <img 
                                class="rounded-full ml-1 min-w-w[35px] max-h-[35px] cursor-pointer" 
                                :src="user.image"
                            />
                            <span>{{ user.name }}</span>
                        </div>
                    </Link>
                    <Link 
                        class="w-full"
                        :href="route('logout')"
                        as="button"
                        method="post"
                        >

                        <div class="flex items-center gap-3 hover:bg-gray-200 px-2 py-2.5 rounded-lg">
                            <Logout class="pl-2" :size="30" />
                            <span>Logout</span>
                        </div>
                    </Link>
                    <div class="text-xs font-semibold p-2 pt-3 border-t mt-1">
                        Privacy · Terms · Advertising · Ad Choices · Cookies · UniConnect © 2023
                    </div>
                </div>
            </div>
        </div>
    </div>

    
    <slot />

    <CreatePostOverlay 
        v-if="isPostOverlay"
        @showModal="isPostOverlay= false"
    />

    <CropperModal 
        v-if="isCropperModal"
        @showModal="isCropperModal = false"
    />

    <ImageDisplay 
        v-if="isImageDisplay"
    />
    
</template>
