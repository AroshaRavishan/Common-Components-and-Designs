<script setup>
import {
    ref,
    onMounted
} from 'vue';
import Preline from "preline";

const isOpen = ref(false);
const isDrawerOpen = ref(false);

const toggleMenu = () => {
    isOpen.value = !isOpen.value;
};

const toggleDrawer = () => {
    isDrawerOpen.value = !isDrawerOpen.value;
};

const closeMobileMenu = () => {
    isOpen.value = false;
};

onMounted(() => {
    initFlowbite();
});
</script>

<template>
    <nav class="bg-beige-300 py-4 sticky w-full top-0 z-10">
        <div class="container flex items-center justify-between">
            <div class="flex-shrink-0 flex gap-6 xl:gap-14 items-center">
                <img data-v-6f3933da="" loading="lazy" alt="GelLogo" class="w-[180px]" src="https://i.imghippo.com/files/LzYzY1720858499.png">
                <div class="hidden lg:block">
                    <button @click="toggleDrawer" class="text-black-900 text-base font-bold flex items-center gap-1 py-4">
                        Drawer Toggle
                        <img loading="lazy" :src="$page.props.assetURL ? $page.props.assetURL + '/web-assets/WebRevamp/arrowdown.svg' : '../../web-assets/WebRevamp/arrowdown.svg'" alt="arrowdown" class="">
                    </button>
                </div>
            </div>
            <div class="hidden lg:flex gap-1 xl:gap-6">
                <div class="flex">
                    <ul class="flex space-x-4 items-center">
                        <li>
                            <router-link to="#Corporate" class="text-black-900 text-base font-bold">Sample Link</router-link>
                        </li>
                        <li>
                            <router-link to="#Instructor" class="text-black-900 text-base font-bold">Sample Lin 2</router-link>
                        </li>
                    </ul>
                </div>
                <div class="hidden lg:block">
                    <div class="flex items-center space-x-4">
                        <router-link to="#Login" class="rounded-lg text-black-900 text-base font-semibold py-2.5 px-6 hover:text-black-500 flex gap-2 items-center border border-transparent hover:border-black-900 cursor-pointer transition-all duration-300 ease-in-out">
                            Login
                            <img loading="lazy" :src="$page.props.assetURL ? $page.props.assetURL + '/web-assets/Arrow-Up.svg' : '../../web-assets/Arrow-Up.svg'" alt="Arrow-Up svg" class="">
                        </router-link>
                    </div>
                </div>
                <div class="hidden lg:block">
                    <div class="flex items-center space-x-4">
                        <router-link to="#Register" class="rounded-lg border border-black-800 text-black-900 text-base font-semibold py-2.5 px-6 hover:text-black-500 cursor-pointer">Register</router-link>
                    </div>
                </div>
            </div>
            <div class="lg:hidden">
                <button @click="toggleMenu" class="block text-black-500 focus:outline-none">
                    <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path v-if="isOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                        <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
                    </svg>
                </button>
            </div>
        </div>
        <!-- mobile menu -->
        <transition enter-active-class="transition-all ease-out duration-700" enter-from-class="opacity-0 max-h-0" enter-to-class="opacity-100 max-h-[400px]" leave-active-class="transition-all ease-in duration-700" leave-from-class="opacity-100 max-h-[400px]" leave-to-class="opacity-0 max-h-0">
            <div v-show="isOpen" class="absolute right-0 w-full bg-beige-300 rounded-b-lg shadow-lg z-50 lg:hidden mt-4 overflow-hidden">
                <ul class="container flex flex-col space-y-2 items-center px-5 py-3">
                    <li class="py-3 w-full">
                        <router-link to="#Corporate" @click="closeMobileMenu" class="text-black-900 text-base font-medium block">
                            Sample Link
                        </router-link>
                    </li>
                    <li class="py-3 w-full">
                        <router-link to="#Instructor" @click="closeMobileMenu" class="text-black-900 text-base font-medium block">
                            Sample Link 2
                        </router-link>
                    </li>
                    <li class="py-3 w-full">
                        <router-link to="#Login" @click="closeMobileMenu" class="text-black-900 text-base font-medium block">
                            Login
                        </router-link>
                    </li>
                    <li class="py-3 w-full">
                        <router-link to="#Register" @click="closeMobileMenu" class="text-black-900 text-base font-medium block">
                            Register
                        </router-link>
                    </li>
                </ul>
            </div>
        </transition>
    </nav>

    <!-- Drawer -->
    <transition
        enter-active-class="transition ease-out duration-300"
        enter-from-class="opacity-0 translate-x-full"
        enter-to-class="opacity-100 translate-x-0"
        leave-active-class="transition ease-in duration-300"
        leave-from-class="opacity-100 translate-x-0"
        leave-to-class="opacity-0 translate-x-full"
    >
        <div v-if="isDrawerOpen" class="fixed inset-0 overflow-hidden z-50">
            <div class="absolute inset-0 overflow-hidden">
                <div class="absolute inset-0 bg-gray-500 bg-opacity-75 transition-opacity" @click="toggleDrawer"></div>
                <section class="absolute inset-y-0 right-0 pl-10 max-w-full flex">
                    <div class="w-screen max-w-md">
                        <div class="h-full flex flex-col bg-white shadow-xl overflow-y-scroll">
                            <div class="p-6">
                                <h2 class="text-lg font-medium text-gray-900">Explore Courses</h2>
                                <button @click="toggleDrawer" class="absolute top-4 right-4">
                                    <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                                    </svg>
                                </button>
                            </div>
                            <div class="flex-1 p-6">
                                <div class="sm:grid sm:grid-cols-1 gap-4">
                                    <div class="flex flex-col">
                                        <a class="flex items-center gap-x-3.5 py-2 px-3 rounded-lg text-sm text-gray-800 hover:bg-gray-100 focus:ring-2 focus:ring-blue-500" href="#">
                                            About
                                        </a>
                                        <a class="flex items-center gap-x-3.5 py-2 px-3 rounded-lg text-sm text-gray-800 hover:bg-gray-100 focus:ring-2 focus:ring-blue-500" href="#">
                                            Services
                                        </a>
                                        <a class="flex items-center gap-x-3.5 py-2 px-3 rounded-lg text-sm text-gray-800 hover:bg-gray-100 focus:ring-2 focus:ring-blue-500" href="#">
                                            Customer Story
                                        </a>
                                    </div>
                                    <div class="flex flex-col">
                                        <a class="flex items-center gap-x-3.5 py-2 px-3 rounded-lg text-sm text-gray-800 hover:bg-gray-100 focus:ring-2 focus:ring-blue-500" href="#">
                                            Careers
                                        </a>
                                        <a class="flex items-center gap-x-3.5 py-2 px-3 rounded-lg text-sm text-gray-800 hover:bg-gray-100 focus:ring-2 focus:ring-blue-500" href="#">
                                            Careers: Overview
                                        </a>
                                        <a class="flex items-center gap-x-3.5 py-2 px-3 rounded-lg text-sm text-gray-800 hover:bg-gray-100 focus:ring-2 focus:ring-blue-500" href="#">
                                            Careers: Apply
                                        </a>
                                    </div>
                                    <div class="flex flex-col">
                                        <a class="flex items-center gap-x-3.5 py-2 px-3 rounded-lg text-sm text-gray-800 hover:bg-gray-100 focus:ring-2 focus:ring-blue-500" href="#">
                                            Log In
                                        </a>
                                        <a class="flex items-center gap-x-3.5 py-2 px-3 rounded-lg text-sm text-gray-800 hover:bg-gray-100 focus:ring-2 focus:ring-blue-500" href="#">
                                            Sign Up
                                        </a>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </section>
            </div>
        </div>
    </transition>
</template>

<style scoped>
.transition-all {
    transition-property: all;
}

.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.3s;
}

.fade-enter,
.fade-leave-to {
    opacity: 0;
}
</style>