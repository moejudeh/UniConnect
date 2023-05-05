<script setup>
import { toRefs, reactive, ref } from 'vue';
import { Link, router } from '@inertiajs/vue3';
const props = defineProps({
    orgName: String,
    orgImage: String,
    orgLink: String,
});
let following = ref(false)
</script>

<template>   
    <div id="orgbox" class="flex gap-10 max-w-md w-[500px] h-[200px] bg-neutral-100 rounded-md p-10 shadow-md m-10 items-center justify-center">
        <span>
            <img class="club-image max-w-[80px]" :src="orgImage" alt="missing image" />
        </span>
        <p class="org-name text-lg">{{orgName}}</p>
        <div class="grid gap-5">
            <a :href="orgLink" target="_blank">
                <button class="rounded-full bg-gray-300 hover:bg-purple-600 w-[105px] py-1">
                    <p class="text-black">website</p>
                </button>
            </a>
            <button 
                v-if="!following" class="rounded-full bg-gray-300 hover:bg-purple-600 w-[105px] py-1" 
                @click="following = !following">
                <p class="text-black">follow</p>
            
            </button>
            <button 
                v-if="following" class="rounded-full w-[105px] py-1 bg-slate-300 outline-4 outline-slate-800 outline-offset-2 bg-purple-600" 
                @click="following = !following">
                <p>unfollow</p>
            </button>
        </div>
    </div>
</template>

<style scoped>
.org-container {
  display: inline-block;
  margin: 10px;
}
.org-logo {
  display: inline;
  max-width: 100%;
  margin-bottom: 10px;
}
.org-name {
  margin: 0;
  font-size: 20px;
}
.follow-button {
    position: relative;
    left:-20px;
    top:30px;
}
</style>
