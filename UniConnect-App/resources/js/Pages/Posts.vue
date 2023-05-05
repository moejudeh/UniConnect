<script setup>
import { usePage, Head , Link } from '@inertiajs/vue3';
import MainNavLayout from '@/Layouts/MainNavLayout.vue';
import CreatePostBox from '@/Components/CreatePostBox.vue'
import Post from '@/Components/Post.vue'


import Magnify from 'vue-material-design-icons/Magnify.vue'
import DotsHorizontal from 'vue-material-design-icons/DotsHorizontal.vue'
import AccountGroup from 'vue-material-design-icons/AccountGroup.vue'
import Chat from 'vue-material-design-icons/Chat.vue'
import Contacts from 'vue-material-design-icons/Contacts.vue'

defineProps({posts: Object})
const user = usePage().props.auth.user
</script>

<template>
    <Head title="UniConnect" />

    <MainNavLayout>
        <div class="fixed w-full h-[100%] bg-[#F1F2F5] mt-[80px]">
            <div class="grid grid-rows-3 grid-flow-col w-full max-w-[1600px] mt-[80px] h-[calc(100%-56px)] mx-auto px-4">
                <div id="Left-Section" class="xl:w-[250px] lg:block hidden ">
                    <div class="pt-4 max-w[320px] pr-4">
                       <Link href="/" 
                        class="flex items-center justify-start w-full cursor-pointer hover:bg-[#E5E6E9] p-2 rounded-md transition-[.8]" >
                          <img id= "UICLogo" class="rounded-full ml-1 min-w-[38px] max-h-[38px]" :src="user.image">
                          <div class="text-[15px] text-gray-800 font-extrabold pl-3">{{ user.name }}</div>
                       </Link>
                       <button class="mr-[10px] flex items-center justify-start w-full cursor-pointer hover:bg-[#E5E6E9] px-2 py-1.5 rounded-md">
                            <Contacts :size="35" fillColor="#5BD7C6"/>
                            <div class="text-[15px] text-gray-800 font-extrabold pl-3">Friends</div>
                        </button>
                        <button class="flex items-center justify-start w-full cursor-pointer hover:bg-[#E5E6E9] px-2 py-1.5 rounded-md ">
                            <AccountGroup :size="35" fillColor="#9b111e"/>
                            <div class="text-[15px] text-gray-800 font-extrabold pl-3">Clubs</div>
                        </button>
                        <button class="flex items-center justify-start w-full cursor-pointer hover:bg-[#E5E6E9] px-2 py-1.5 rounded-md">
                            <Chat :size="35" fillColor="#FFFF00"/>
                            <div class="text-[15px] text-gray-800 font-extrabold pl-3">Chat</div>
                        </button>
                    </div>
                </div>
                <div id ="PostsSection" class = "xl:w-[600px] items-center row-span-6 lg:mx-5 mx-auto overflow-auto">
                    <CreatePostBox 
                        :image= "user.image"
                        placeholder="Post Something :D"
                    />
                    <div v-for="post in posts.data" :key="post">
                        <Post :user="post.user" :post="post" :comments="post.comments"/>
                    </div> 
                </div>
                <div id="RightSection" class="pl-20 md:block hidden">
                    <div class="max-w-[350px] min-w-[85px] mx-auto-pt-4">
                        <div class="flex items-center justify-between border-b border-b-gray-300">
                            <div class="font-semibold">Friends</div>
                            <div class="flex items-center">
                                <div class="p-2 hover:bg-gray-300 rounded-full cursor-pointer">
                                    <div>
                                        <Magnify :size="23" fillColor="#050505"/>
                                    </div>
                                </div>
                                <div class="p-2 hover:bg-gray-300 rounded-full cursor-pointer">
                                    <div>
                                        <DotsHorizontal :size="23" fillColor="#050505"/>
                                    </div>
                                </div>
                            </div> 
                        </div>
                        <div class="overflow-auto pt-2">
                            <div class="flex item-center justify-start cursor-pointer hover:bg-[#E5E6E9] py-2 rounded-md">
                                  <img class="rounded-full ml-1 min-w-[38px] max-h-[38px]" src="https://picsum.photos/id/140/300/320">
                                  <div class=" mt-[10px] ml-[15px]">John Doe</div>
                            </div>
                        </div>
                        <div class="overflow-auto pt-2">
                            <div class="flex item-center justify-start cursor-pointer hover:bg-[#E5E6E9] py-2 rounded-md">
                                  <img class="rounded-full ml-1 min-w-[38px] max-h-[38px]" src="https://picsum.photos/id/141/300/320">
                                  <div class=" mt-[10px] ml-[15px]"> Matheo Sibusiso</div>
                            </div>
                        </div>
                        <div class="overflow-auto pt-2">
                            <div class="flex item-center justify-start cursor-pointer hover:bg-[#E5E6E9] py-2 rounded-md">
                                  <img class="rounded-full ml-1 min-w-[38px] max-h-[38px]" src="https://picsum.photos/id/142/300/320">
                                  <div class=" mt-[10px] ml-[15px]">Terrance Mcgee</div>
                            </div>
                        </div>
                        <div class="overflow-auto pt-2">
                            <div class="flex item-center justify-start cursor-pointer hover:bg-[#E5E6E9] py-2 rounded-md">
                                  <img class="rounded-full ml-1 min-w-[38px] max-h-[38px]" src="https://picsum.photos/id/143/300/320">
                                  <div class=" mt-[10px] ml-[15px]">Joan Joseph</div>
                            </div>
                        </div>
                        <div class="overflow-auto pt-2">
                            <div class="flex item-center justify-start cursor-pointer hover:bg-[#E5E6E9] py-2 rounded-md">
                                  <img class="rounded-full ml-1 min-w-[38px] max-h-[38px]" src="https://picsum.photos/id/144/300/320">
                                  <div class=" mt-[10px] ml-[15px]">Erin Tucker</div>
                            </div>
                        </div>
                        <div class="overflow-auto pt-2">
                            <div class="flex item-center justify-start cursor-pointer hover:bg-[#E5E6E9] py-2 rounded-md">
                                  <img class="rounded-full ml-1 min-w-[38px] max-h-[38px]" src="https://picsum.photos/id/145/300/320">
                                  <div class=" mt-[10px] ml-[15px]">Darnell Francis</div>
                            </div>
                        </div>
                        <div class="overflow-auto pt-2">
                            <div class="flex item-center justify-start cursor-pointer hover:bg-[#E5E6E9] py-2 rounded-md">
                                  <img class="rounded-full ml-1 min-w-[38px] max-h-[38px]" src="https://picsum.photos/id/146/300/320">
                                  <div class=" mt-[10px] ml-[15px]">Tracy Gray</div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </MainNavLayout>

</template>
