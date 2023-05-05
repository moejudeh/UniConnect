<script setup>
import { Link } from '@inertiajs/vue3';
</script>

<template>
    <div class="min-h-screen flex flex-col sm:justify-center items-center pt-6 sm:pt-0 bg-purple-700">
        <div>
            <Link :href="route('login')">
                <img class="w-[200px] h-[200px] fill-current text-gray-500"  src="https://i.ibb.co/w6r4y86/Uni-Connect-1-white.png"/>
            </Link>
        </div>

        <div
            class="w-full sm:max-w-md  px-6 py-4 bg-white shadow-md overflow-hidden sm:rounded-lg"
        >
            <slot />
        </div>
    </div>
</template>
