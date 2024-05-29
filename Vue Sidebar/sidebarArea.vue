<script setup>
import { ref, watch, onMounted } from 'vue';
import { Link, usePage } from '@inertiajs/vue3';

const props = defineProps({
    toggleSize: {
        type: Boolean,
        default: true,
    },
});

const selected = ref(0);
const isEnlarge = ref(true);
const dropdownOpen = ref(false);
const dropdownIndex = ref(null);

watch(() => props.toggleSize, (value) => {
    isEnlarge.value = value;
    previouseStatus.value = value;
});

const toggleDropdown = (index) => {
    if (dropdownOpen.value && dropdownIndex.value === index) {
        dropdownOpen.value = false;
        dropdownIndex.value = null;
    } else {
        dropdownOpen.value = true;
        dropdownIndex.value = index;
        selected.value = index;
    }

    if (event) {
        event.preventDefault();
    }

    localStorage.setItem('dropdownState', JSON.stringify({
        dropdownOpen: dropdownOpen.value,
        dropdownIndex: dropdownIndex.value,
        selected: selected.value
    }));
};

const retrieveDropdownState = () => {
    const savedState = JSON.parse(localStorage.getItem('dropdownState'));
    if (savedState) {
        dropdownOpen.value = savedState.dropdownOpen;
        dropdownIndex.value = savedState.dropdownIndex;
        selected.value = savedState.selected;
    }
};

// Call retrieveDropdownState when the component is created
onMounted(() => {
    retrieveDropdownState();
});

const nav = [{
    icon: '<svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><g clip-path="url(#clip0_86_662)"><path d="M19 5V7H15V5H19ZM9 5V11H5V5H9ZM19 13V19H15V13H19ZM9 17V19H5V17H9ZM21 3H13V9H21V3ZM11 3H3V13H11V3ZM21 11H13V21H21V11ZM11 15H3V21H11V15Z" fill="#666666"/></g><defs><clipPath id="clip0_86_662"><rect width="24" height="24" fill="white"/></clipPath></defs></svg>',
    selectedIcon: '<svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor" xmlns="http://www.w3.org/2000/svg"><g clip-path="url(#clip0_86_662)"><path d="M19 5V7H15V5H19ZM9 5V11H5V5H9ZM19 13V19H15V13H19ZM9 17V19H5V17H9ZM21 3H13V9H21V3ZM11 3H3V13H11V3ZM21 11H13V21H21V11ZM11 15H3V21H11V15Z" fill="#currentColor"/></g><defs><clipPath id="clip0_86_662"><rect width="24" height="24" fill="white"/></clipPath></defs></svg>',
    text: "Overview"
},
{
    icon: '<svg width="20" height="20" viewBox="0 0 20 16" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M7.17 2L9.17 4H18V14H2V2H7.17ZM8 0H2C0.9 0 0.00999999 0.9 0.00999999 2L0 14C0 15.1 0.9 16 2 16H18C19.1 16 20 15.1 20 14V4C20 2.9 19.1 2 18 2H10L8 0Z" fill="#666666"/></svg>',
    selectedIcon: '<svg width="20" height="20" viewBox="0 0 20 16" fill="currentColor" xmlns="http://www.w3.org/2000/svg"><path d="M7.17 2L9.17 4H18V14H2V2H7.17ZM8 0H2C0.9 0 0.00999999 0.9 0.00999999 2L0 14C0 15.1 0.9 16 2 16H18C19.1 16 20 15.1 20 14V4C20 2.9 19.1 2 18 2H10L8 0Z" fill="#currentColor"/></svg>',
    text: "Courses"
},
{
    icon: '<svg width="20" viewBox="0 0 20 14" fill="none" xmlns="http://www.w3.org/2000/svg" height="20"><path d="M7 7C8.93 7 10.5 5.43 10.5 3.5C10.5 1.57 8.93 0 7 0C5.07 0 3.5 1.57 3.5 3.5C3.5 5.43 5.07 7 7 7ZM7 2C7.83 2 8.5 2.67 8.5 3.5C8.5 4.33 7.83 5 7 5C6.17 5 5.5 4.33 5.5 3.5C5.5 2.67 6.17 2 7 2ZM7.05 12H2.77C3.76 11.5 5.47 11 7 11C7.11 11 7.23 11.01 7.34 11.01C7.68 10.28 8.27 9.68 8.98 9.2C8.25 9.07 7.56 9 7 9C4.66 9 0 10.17 0 12.5V14H7V12.5C7 12.33 7.02 12.16 7.05 12ZM14.5 9.5C12.66 9.5 9 10.51 9 12.5V14H20V12.5C20 10.51 16.34 9.5 14.5 9.5ZM15.71 7.68C16.47 7.25 17 6.44 17 5.5C17 4.12 15.88 3 14.5 3C13.12 3 12 4.12 12 5.5C12 6.44 12.53 7.25 13.29 7.68C13.65 7.88 14.06 8 14.5 8C14.94 8 15.35 7.88 15.71 7.68Z" fill="#666666"></path></svg>',
    selectedIcon: '<svg width="20" viewBox="0 0 20 14" fill="currentColor" xmlns="http://www.w3.org/2000/svg" height="20"><path d="M7 7C8.93 7 10.5 5.43 10.5 3.5C10.5 1.57 8.93 0 7 0C5.07 0 3.5 1.57 3.5 3.5C3.5 5.43 5.07 7 7 7ZM7 2C7.83 2 8.5 2.67 8.5 3.5C8.5 4.33 7.83 5 7 5C6.17 5 5.5 4.33 5.5 3.5C5.5 2.67 6.17 2 7 2ZM7.05 12H2.77C3.76 11.5 5.47 11 7 11C7.11 11 7.23 11.01 7.34 11.01C7.68 10.28 8.27 9.68 8.98 9.2C8.25 9.07 7.56 9 7 9C4.66 9 0 10.17 0 12.5V14H7V12.5C7 12.33 7.02 12.16 7.05 12ZM14.5 9.5C12.66 9.5 9 10.51 9 12.5V14H20V12.5C20 10.51 16.34 9.5 14.5 9.5ZM15.71 7.68C16.47 7.25 17 6.44 17 5.5C17 4.12 15.88 3 14.5 3C13.12 3 12 4.12 12 5.5C12 6.44 12.53 7.25 13.29 7.68C13.65 7.88 14.06 8 14.5 8C14.94 8 15.35 7.88 15.71 7.68Z" fill="#currentColor"></path></svg>',
    text: "User Accounts"
},
{
    icon: '<svg width="16" height="20" viewBox="0 0 16 20" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M10 0H2C0.9 0 0.0100002 0.9 0.0100002 2L0 18C0 19.1 0.89 20 1.99 20H14C15.1 20 16 19.1 16 18V6L10 0ZM2 18V2H9V7H14V18H2Z" fill="#666666"/></svg>',
    selectedIcon: '<svg width="16" height="20" viewBox="0 0 16 20" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M10 0H2C0.9 0 0.0100002 0.9 0.0100002 2L0 18C0 19.1 0.89 20 1.99 20H14C15.1 20 16 19.1 16 18V6L10 0ZM2 18V2H9V7H14V18H2Z" fill="currentColor"/></svg>',
    text: "Resources"
},
{
    icon: '<svg width="20" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M4 5H0V16H4V5Z" fill="#666666"/><path d="M4 0H0V4H4V0Z" fill="#666666"/><path d="M10 3H6V7H10V3Z" fill="#666666"/><path d="M16 6H12V10H16V6Z" fill="#666666"/><path d="M16 11H12V16H16V11Z" fill="#666666"/><path d="M10 8H6V16H10V8Z" fill="#666666"/></svg>',
    selectedIcon: '<svg width="20" height="16" viewBox="0 0 16 16" fill="currentColor" xmlns="http://www.w3.org/2000/svg"><path d="M4 5H0V16H4V5Z" fill="currentColor"/><path d="M4 0H0V4H4V0Z" fill="currentColor"/><path d="M10 3H6V7H10V3Z" fill="currentColor"/><path d="M16 6H12V10H16V6Z" fill="currentColor"/><path d="M16 11H12V16H16V11Z" fill="currentColor"/><path d="M10 8H6V16H10V8Z" fill="currentColor"/></svg>',
    text: "Analytics & Reports"
},
{
    icon: '<svg width="20" viewBox="0 0 20 14" fill="none" xmlns="http://www.w3.org/2000/svg" height="20"><path d="M7 7C8.93 7 10.5 5.43 10.5 3.5C10.5 1.57 8.93 0 7 0C5.07 0 3.5 1.57 3.5 3.5C3.5 5.43 5.07 7 7 7ZM7 2C7.83 2 8.5 2.67 8.5 3.5C8.5 4.33 7.83 5 7 5C6.17 5 5.5 4.33 5.5 3.5C5.5 2.67 6.17 2 7 2ZM7.05 12H2.77C3.76 11.5 5.47 11 7 11C7.11 11 7.23 11.01 7.34 11.01C7.68 10.28 8.27 9.68 8.98 9.2C8.25 9.07 7.56 9 7 9C4.66 9 0 10.17 0 12.5V14H7V12.5C7 12.33 7.02 12.16 7.05 12ZM14.5 9.5C12.66 9.5 9 10.51 9 12.5V14H20V12.5C20 10.51 16.34 9.5 14.5 9.5ZM15.71 7.68C16.47 7.25 17 6.44 17 5.5C17 4.12 15.88 3 14.5 3C13.12 3 12 4.12 12 5.5C12 6.44 12.53 7.25 13.29 7.68C13.65 7.88 14.06 8 14.5 8C14.94 8 15.35 7.88 15.71 7.68Z" fill="#666666"></path></svg>',
    selectedIcon: '<svg width="20" viewBox="0 0 20 14" fill="currentColor" xmlns="http://www.w3.org/2000/svg" height="20"><path d="M7 7C8.93 7 10.5 5.43 10.5 3.5C10.5 1.57 8.93 0 7 0C5.07 0 3.5 1.57 3.5 3.5C3.5 5.43 5.07 7 7 7ZM7 2C7.83 2 8.5 2.67 8.5 3.5C8.5 4.33 7.83 5 7 5C6.17 5 5.5 4.33 5.5 3.5C5.5 2.67 6.17 2 7 2ZM7.05 12H2.77C3.76 11.5 5.47 11 7 11C7.11 11 7.23 11.01 7.34 11.01C7.68 10.28 8.27 9.68 8.98 9.2C8.25 9.07 7.56 9 7 9C4.66 9 0 10.17 0 12.5V14H7V12.5C7 12.33 7.02 12.16 7.05 12ZM14.5 9.5C12.66 9.5 9 10.51 9 12.5V14H20V12.5C20 10.51 16.34 9.5 14.5 9.5ZM15.71 7.68C16.47 7.25 17 6.44 17 5.5C17 4.12 15.88 3 14.5 3C13.12 3 12 4.12 12 5.5C12 6.44 12.53 7.25 13.29 7.68C13.65 7.88 14.06 8 14.5 8C14.94 8 15.35 7.88 15.71 7.68Z" fill="#currentColor"></path></svg>',
    text: "Email Management"
},
{
    icon: '<svg width="21" height="21" viewBox="0 0 18 21" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M16 0H2C0.89 0 0 0.9 0 2V16C0 17.1 0.89 18 2 18H6L9 21L12 18H16C17.1 18 18 17.1 18 16V2C18 0.9 17.1 0 16 0ZM16 16H11.17L10.58 16.59L9 18.17L7.41 16.58L6.83 16H2V2H16V16ZM9 9C10.65 9 12 7.65 12 6C12 4.35 10.65 3 9 3C7.35 3 6 4.35 6 6C6 7.65 7.35 9 9 9ZM9 5C9.55 5 10 5.45 10 6C10 6.55 9.55 7 9 7C8.45 7 8 6.55 8 6C8 5.45 8.45 5 9 5ZM15 13.58C15 11.08 11.03 10 9 10C6.97 10 3 11.08 3 13.58V15H15V13.58ZM5.48 13C6.22 12.49 7.71 12 9 12C10.29 12 11.78 12.49 12.52 13H5.48Z" fill="#666666"/></svg>',
    selectedIcon: '<svg width="21" height="21" viewBox="0 0 18 21" fill="currentColor" xmlns="http://www.w3.org/2000/svg"><path d="M16 0H2C0.89 0 0 0.9 0 2V16C0 17.1 0.89 18 2 18H6L9 21L12 18H16C17.1 18 18 17.1 18 16V2C18 0.9 17.1 0 16 0ZM16 16H11.17L10.58 16.59L9 18.17L7.41 16.58L6.83 16H2V2H16V16ZM9 9C10.65 9 12 7.65 12 6C12 4.35 10.65 3 9 3C7.35 3 6 4.35 6 6C6 7.65 7.35 9 9 9ZM9 5C9.55 5 10 5.45 10 6C10 6.55 9.55 7 9 7C8.45 7 8 6.55 8 6C8 5.45 8.45 5 9 5ZM15 13.58C15 11.08 11.03 10 9 10C6.97 10 3 11.08 3 13.58V15H15V13.58ZM5.48 13C6.22 12.49 7.71 12 9 12C10.29 12 11.78 12.49 12.52 13H5.48Z" fill="#currentColor"/></svg>',
    text: "My Profile"
}
];

const enlarge = {
    decrease: '<svg fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M12.707 5.293a1 1 0 010 1.414L9.414 10l3.293 3.293a1 1 0 01-1.414 1.414l-4-4a1 1 0 010-1.414l4-4a1 1 0 011.414 0z" clip-rule="evenodd"></path></svg>',
    enlarge: '<svg fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z" clip-rule="evenodd"></path></svg>',
    text: "Enlarge"
};

const toggleSize = () => {
    isEnlarge.value = !isEnlarge.value;
};

const isHover = ref(false);

const previouseStatus = ref(props.toggleSize);
const handleMouseEnter = () => {
    if (isEnlarge.value == false) {
        previouseStatus.value = false;
        isEnlarge.value = true;
        isHover.value = true;
    }
};

const handleMouseLeave = () => {
    if (previouseStatus.value == false) {
        isEnlarge.value = false;
        isHover.value = false;
    }
};

</script>

<template>
    <div id="app" class="min-h-screen bg-gray-200">
        <div :class="{ 'large-menu': isEnlarge, 'small-menu': !isEnlarge }">
            <header
                :class="{ 'relative justify-between bg-white shadow p-6 h-screen smoothShow': isHover, 'relative justify-between bg-white shadow p-6 h-screen': !isHover }"
                @mouseenter="handleMouseEnter" @mouseleave="handleMouseLeave">
                <div
                    :class="{ 'flex items-center justify-between border-b pb-4': isEnlarge, 'inline-block border-b pb-2': !isEnlarge }">
                    <div class="icon-hover">
                        <!-- Enlarge Image -->
                        <div class="enlarge-image" v-show="isEnlarge">
                            <img loading="lazy"
                                :src="$page.props.client ? $page.props.client.client_logo_url : '../../web-assets/enlarge-image.jpg'"
                                alt="enlarge-image" class="w-[230px] h-[75px] object-contain">
                        </div>
                        <!-- Decrease Image -->
                        <div class="decrease-image flex items-center" v-show="!isEnlarge">
                            <img loading="lazy"
                                :src="$page.props.client ? $page.props.client.client_favicon_url : '../../web-assets/decrease-image.jpg'"
                                alt="decrease-image" class="w-[50px] h-[70px] object-contain">
                        </div>
                    </div>
                    <!-- <div class="menu-image">
                    <img v-html="isEnlarge ? enlarge.decrease : enlarge.enlarge" loading="lazy"
                        :src="$page.props.assetURL ? $page.props.assetURL + '/web-assets/Menu open.png' : '../../web-assets/Menu open.png'"
                        alt="Menu-image" :class="{ '': isEnlarge, 'mt-3': !isEnlarge }" @click="toggleSize">
                </div> -->
                </div>
                <nav class="mt-8 space-y-2">
                    <!-- Overview -->
                    <div class="icon-hover">
                        <Link :href="route('client.dashboard', { 'client': $page.props.client.slug })"
                            class="flex items-center text-ash-450 py-2 cursor-pointer hover:bg-gray-100 relative text-sm"
                            :class="[{ 'bg-primary !text-primary border border-primary shade-class': selected === 0 }, isEnlarge ? 'pl-2 pr-6 rounded-lg' : 'px-2 rounded-lg']"
                            @click="toggleDropdown(0)">
                        <span v-html="selected === 0 ? nav[0].selectedIcon : nav[0].icon" class="w-8 h-8 p-1"
                            :class="{ 'mr-1': isEnlarge }"></span>
                        <span v-html="nav[0].text" class="font-normal select-none" v-if="isEnlarge"></span>
                        <img src="https://cdn-icons-png.flaticon.com/128/2722/2722985.png" loading="lazy" alt="Right"
                            title="Right" width="20" height="20"
                            class="w-8 h-8 p-1 absolute right-0 right-chevron-icon hidden"
                            :class="{ 'mr-0': isEnlarge, 'hidden': !isEnlarge, 'rotate-90': dropdownOpen && dropdownIndex === 0 }">
                        </Link>
                        <transition name="dropdown">
                            <ul v-show="dropdownOpen && dropdownIndex === 0 && isEnlarge" class="ml-5">
                                <!-- Add more sub nav items here -->
                            </ul>
                        </transition>
                    </div>
                    <!-- Courses -->
                    <div class="icon-hover">
                        <a class="flex items-center text-ash-450 py-2 cursor-pointer hover:bg-gray-100 relative text-sm"
                            :class="[{ 'bg-primary !text-primary border border-primary shade-class': selected === 1 }, isEnlarge ? 'pl-2 pr-6 rounded-lg' : 'px-2 rounded-lg']"
                            @click="toggleDropdown(1)">
                            <span v-html="selected === 1 ? nav[1].selectedIcon : nav[1].icon" class="w-8 h-8 p-1"
                                :class="{ 'mr-1': isEnlarge }"></span>
                            <span v-html="nav[1].text" class="font-normal select-none" v-if="isEnlarge"></span>
                            <img src="https://cdn-icons-png.flaticon.com/128/2722/2722985.png" loading="lazy"
                                alt="Right" title="Right" width="20" height="20"
                                class="w-8 h-8 p-1 absolute right-0 right-chevron-icon"
                                :class="{ 'mr-0': isEnlarge, 'hidden': !isEnlarge, 'rotate-90': dropdownOpen && dropdownIndex === 1 }">
                        </a>
                        <transition name="dropdown">
                            <ul v-show="dropdownOpen && dropdownIndex === 1 && isEnlarge" class="ml-5">
                                <ol class="relative border-s border-primary dark:border-gray-700">
                                    <li class="mb-6 ms-4 pt-3">
                                        <div
                                            class="absolute w-3 h-3 bg-white rounded-full mt-1.5 -start-1.5 border-3 border-primary dark:border-gray-900 dark:bg-gray-700">
                                        </div>
                                        <Link
                                            :href="route('client.page.managecourse', { 'client': $page.props.client.slug })"
                                            class="sub-navitems-dropdown"><time
                                            class="mb-1 text-sm font-normal leading-none text-gray-400 dark:text-gray-500">Manage
                                            Courses</time></Link>
                                    </li>
                                    <li class="mb-6 ms-4 hidden">
                                        <div
                                            class="absolute w-3 h-3 bg-white rounded-full mt-1.5 -start-1.5 border-3 border-primary dark:border-gray-900 dark:bg-gray-700">
                                        </div>
                                        <Link
                                            :href="route('client.page.managecertificates', { 'client': $page.props.client.slug })"
                                            class="sub-navitems-dropdown">
                                        <time
                                            class="mb-1 text-sm font-normal leading-none text-gray-400 dark:text-gray-500">Manage
                                            Certificates</time></Link>
                                    </li>
                                    <li class="ms-4 hidden">
                                        <div
                                            class="absolute w-3 h-3 bg-white rounded-full mt-1.5 -start-1.5 border-3 border-primary dark:border-gray-900 dark:bg-gray-700">
                                        </div>
                                        <a class="sub-navitems-dropdown"><time
                                                class="mb-1 text-sm font-normal leading-none text-gray-400 dark:text-gray-500">February
                                                2022</time></a>
                                    </li>
                                </ol>
                            </ul>
                        </transition>
                    </div>
                    <!-- Accounts -->
                    <div class="icon-hover">
                        <a class="flex items-center text-ash-450 py-2 cursor-pointer hover:bg-gray-100 relative text-sm"
                            :class="[{ 'bg-primary !text-primary border border-primary shade-class': selected === 2 }, isEnlarge ? 'pl-2 pr-6 rounded-lg' : 'px-2 rounded-lg']"
                            @click="toggleDropdown(2)">
                            <span v-html="selected === 2 ? nav[2].selectedIcon : nav[2].icon" class="w-8 h-8 p-1"
                                :class="{ 'mr-1': isEnlarge }"></span>
                            <span v-html="nav[2].text" class="font-normal select-none" v-if="isEnlarge"></span>
                            <img src="https://cdn-icons-png.flaticon.com/128/2722/2722985.png" loading="lazy"
                                alt="Right" title="Right" width="20" height="20"
                                class="w-8 h-8 p-1 absolute right-0 right-chevron-icon"
                                :class="{ 'mr-0': isEnlarge, 'hidden': !isEnlarge, 'rotate-90': dropdownOpen && dropdownIndex === 2 }">
                        </a>
                        <transition name="dropdown">
                            <ul v-show="dropdownOpen && dropdownIndex === 2 && isEnlarge" class="ml-5">
                                <ol class="relative border-s border-primary dark:border-gray-700">
                                    <li class="mb-6 ms-4 pt-3">
                                        <div
                                            class="absolute w-3 h-3 bg-white rounded-full mt-1.5 -start-1.5 border-3 border-primary dark:border-gray-900 dark:bg-gray-700">
                                        </div>
                                        <Link
                                            :href="route('client.student.index', { 'client': $page.props.client.slug })"
                                            class="sub-navitems-dropdown">
                                        <time
                                            class="mb-1 text-sm font-normal leading-none text-gray-400 dark:text-gray-500">Students</time>
                                        </Link>
                                    </li>
                                    <li class="ms-4">
                                        <div
                                            class="absolute w-3 h-3 bg-white rounded-full mt-1.5 -start-1.5 border-3 border-primary dark:border-gray-900 dark:bg-gray-700">
                                        </div>
                                        <Link
                                            :href="route('client.admins.index', { 'client': $page.props.client.slug })"
                                            class="sub-navitems-dropdown"><time
                                            class="mb-1 text-sm font-normal leading-none text-gray-400 dark:text-gray-500">Admins</time>
                                        </Link>
                                    </li>
                                </ol>
                            </ul>
                        </transition>
                    </div>
                    <!-- Resources -->
                    <div class="icon-hover">
                        <a class="flex items-center text-ash-450 py-2 cursor-pointer hover:bg-gray-100 relative text-sm"
                            :class="[{ 'bg-primary !text-primary border border-primary shade-class': selected === 3 }, isEnlarge ? 'pl-2 pr-6 rounded-lg' : 'px-2 rounded-lg']"
                            @click="toggleDropdown(3)">
                            <span v-html="selected === 3 ? nav[3].selectedIcon : nav[3].icon" class="w-8 h-8 p-1"
                                :class="{ 'mr-1': isEnlarge }"></span>
                            <span v-html="nav[3].text" class="font-normal select-none" v-if="isEnlarge"></span>
                            <img src="https://cdn-icons-png.flaticon.com/128/2722/2722985.png" loading="lazy"
                                alt="Right" title="Right" width="20" height="20"
                                class="w-8 h-8 p-1 absolute right-0 right-chevron-icon"
                                :class="{ 'mr-0': isEnlarge, 'hidden': !isEnlarge, 'rotate-90': dropdownOpen && dropdownIndex === 3 }">
                        </a>
                        <transition name="dropdown">
                            <ul v-show="dropdownOpen && dropdownIndex === 3 && isEnlarge" class="ml-5">
                                <ol class="relative border-s border-primary dark:border-gray-700">
                                    <li class="mb-6 ms-4 pt-3">
                                        <div
                                            class="absolute w-3 h-3 bg-white rounded-full mt-1.5 -start-1.5 border-3 border-primary dark:border-gray-900 dark:bg-gray-700">
                                        </div>
                                        <Link
                                            :href="route('client.page.clientdetails', { 'client': $page.props.client.slug })"
                                            class="sub-navitems-dropdown"><time
                                            class="mb-1 text-sm font-normal leading-none text-gray-400 dark:text-gray-500">Course
                                            Details</time></Link>
                                    </li>
                                    <li class="mb-6 ms-4">
                                        <div
                                            class="absolute w-3 h-3 bg-white rounded-full mt-1.5 -start-1.5 border-3 border-primary dark:border-gray-900 dark:bg-gray-700">
                                        </div>
                                        <Link
                                            :href="route('client.page.clientpresentation', { 'client': $page.props.client.slug })"
                                            class="sub-navitems-dropdown"><time
                                            class="mb-1 text-sm font-normal leading-none text-gray-400 dark:text-gray-500">Presentations</time>
                                        </Link>
                                    </li>
                                    <li class="mb-6 ms-4">
                                        <div
                                            class="absolute w-3 h-3 bg-white rounded-full mt-1.5 -start-1.5 border-3 border-primary dark:border-gray-900 dark:bg-gray-700">
                                        </div>
                                        <Link
                                            :href="route('client.page.clientguides', { 'client': $page.props.client.slug })"
                                            class="sub-navitems-dropdown"><time
                                            class="mb-1 text-sm font-normal leading-none text-gray-400 dark:text-gray-500">Guides</time>
                                        </Link>
                                    </li>
                                    <li class="ms-4">
                                        <div
                                            class="absolute w-3 h-3 bg-white rounded-full mt-1.5 -start-1.5 border-3 border-primary dark:border-gray-900 dark:bg-gray-700">
                                        </div>
                                        <Link
                                            :href="route('client.page.clientsamplecertification', { 'client': $page.props.client.slug })"
                                            class="sub-navitems-dropdown"><time
                                            class="mb-1 text-sm font-normal leading-none text-gray-400 dark:text-gray-500">Sample
                                            Certifications</time></Link>
                                    </li>
                                </ol>
                            </ul>
                        </transition>
                    </div>
                    <!-- Analytics & Reports -->
                    <div class="icon-hover">
                        <a class="flex items-center text-ash-450 py-2 cursor-pointer hover:bg-gray-100 relative text-sm"
                            :class="[{ 'bg-primary !text-primary border border-primary shade-class': selected === 4 }, isEnlarge ? 'pl-2 pr-6 rounded-lg' : 'px-2 rounded-lg']"
                            @click="toggleDropdown(4)">
                            <span v-html="selected === 4 ? nav[4].selectedIcon : nav[4].icon" class="w-8 h-8 p-1"
                                :class="{ 'mr-1': isEnlarge }"></span>
                            <span v-html="nav[4].text" class="font-normal select-none" v-if="isEnlarge"></span>
                            <img src="https://cdn-icons-png.flaticon.com/128/2722/2722985.png" loading="lazy"
                                alt="Right" title="Right" width="20" height="20"
                                class="w-8 h-8 p-1 absolute right-0 right-chevron-icon"
                                :class="{ 'mr-0': isEnlarge, 'hidden': !isEnlarge, 'rotate-90': dropdownOpen && dropdownIndex === 4 }">
                        </a>
                        <transition name="dropdown">
                            <ul v-show="dropdownOpen && dropdownIndex === 4 && isEnlarge" class="ml-5">
                                <ol class="relative border-s border-primary dark:border-gray-700">
                                    <li class="mb-6 ms-4 pt-3">
                                        <div
                                            class="absolute w-3 h-3 bg-white rounded-full mt-1.5 -start-1.5 border-3 border-primary dark:border-gray-900 dark:bg-gray-700">
                                        </div>
                                        <a class="sub-navitems-dropdown"><time
                                                class="mb-1 text-sm font-normal leading-none text-gray-400 dark:text-gray-500">Payments</time></a>
                                    </li>
                                    <li class="mb-6 ms-4">
                                        <div
                                            class="absolute w-3 h-3 bg-white rounded-full mt-1.5 -start-1.5 border-3 border-primary dark:border-gray-900 dark:bg-gray-700">
                                        </div>
                                        <a class="sub-navitems-dropdown">
                                            <time
                                                class="mb-1 text-sm font-normal leading-none text-gray-400 dark:text-gray-500">User
                                                Reports</time></a>
                                    </li>
                                    <li class="ms-4">
                                        <div
                                            class="absolute w-3 h-3 bg-white rounded-full mt-1.5 -start-1.5 border-3 border-primary dark:border-gray-900 dark:bg-gray-700">
                                        </div>
                                        <a class="sub-navitems-dropdown"><time
                                                class="mb-1 text-sm font-normal leading-none text-gray-400 dark:text-gray-500">Course
                                                Reports</time></a>
                                    </li>
                                </ol>
                            </ul>
                        </transition>
                    </div>
                    <!-- Email Management -->
                    <div class="icon-hover">
                        <a class="flex items-center text-ash-450 py-2 cursor-pointer hover:bg-gray-100 relative text-sm"
                            :class="[{ 'bg-primary !text-primary border border-primary shade-class': selected === 5 }, isEnlarge ? 'pl-2 pr-6 rounded-lg' : 'px-2 rounded-lg']"
                            @click="toggleDropdown(5)">
                            <span v-html="selected === 5 ? nav[5].selectedIcon : nav[5].icon" class="w-8 h-8 p-1"
                                :class="{ 'mr-1': isEnlarge }"></span>
                            <span v-html="nav[5].text" class="font-normal select-none" v-if="isEnlarge"></span>
                            <img src="https://cdn-icons-png.flaticon.com/128/2722/2722985.png" loading="lazy"
                                alt="Right" title="Right" width="20" height="20"
                                class="w-8 h-8 p-1 absolute right-0 right-chevron-icon"
                                :class="{ 'mr-0': isEnlarge, 'hidden': !isEnlarge, 'rotate-90': dropdownOpen && dropdownIndex === 5 }">
                        </a>
                        <transition name="dropdown">
                            <ul v-show="dropdownOpen && dropdownIndex === 5 && isEnlarge" class="ml-5">
                                <ol class="relative border-s border-primary dark:border-gray-700">
                                    <li class="mb-6 ms-4 pt-3">
                                        <div
                                            class="absolute w-3 h-3 bg-white rounded-full mt-1.5 -start-1.5 border-3 border-primary dark:border-gray-900 dark:bg-gray-700">
                                        </div>
                                        <Link
                                            :href="route('client.page.clientsemailtemplates', { 'client': $page.props.client.slug })"
                                            class="sub-navitems-dropdown">
                                        <time
                                            class="mb-1 text-sm font-normal leading-none text-gray-400 dark:text-gray-500">Email
                                            Template</time>
                                        </Link>
                                    </li>
                                    <li class="ms-4">
                                        <div
                                            class="absolute w-3 h-3 bg-white rounded-full mt-1.5 -start-1.5 border-3 border-primary dark:border-gray-900 dark:bg-gray-700">
                                        </div>
                                        <Link
                                            :href="route('client.page.clientsemailtemplatessettings', { 'client': $page.props.client.slug })"
                                            class="sub-navitems-dropdown"><time
                                            class="mb-1 text-sm font-normal leading-none text-gray-400 dark:text-gray-500">Email
                                            Template Settings</time>
                                        </Link>
                                    </li>
                                </ol>
                                <!-- Add more sub nav items here -->
                            </ul>
                        </transition>
                    </div>
                    <!-- My Profile -->
                    <div class="icon-hover">
                        <Link :href="route('client.page.profiledetails', { 'client': $page.props.client.slug })"
                            class="flex items-center text-ash-450 py-2 cursor-pointer hover:bg-gray-100 relative text-sm"
                            :class="[{ 'bg-primary !text-primary border border-primary shade-class': selected === 6 }, isEnlarge ? 'pl-2 pr-6 rounded-lg' : 'px-2 rounded-lg']"
                            @click="toggleDropdown(6)">
                        <span v-html="selected === 6 ? nav[6].selectedIcon : nav[6].icon" class="w-8 h-8 p-1"
                            :class="{ 'mr-1': isEnlarge }"></span>
                        <span v-html="nav[6].text" class="font-normal select-none" v-if="isEnlarge"></span>
                        <img src="https://cdn-icons-png.flaticon.com/128/2722/2722985.png" loading="lazy" alt="Right"
                            title="Right" width="20" height="20"
                            class="w-8 h-8 p-1 absolute right-0 right-chevron-icon hidden"
                            :class="{ 'mr-0': isEnlarge, 'hidden': !isEnlarge, 'rotate-90': dropdownOpen && dropdownIndex === 6 }">
                        </Link>
                        <transition name="dropdown">
                            <ul v-show="dropdownOpen && dropdownIndex === 6 && isEnlarge" class="ml-5">

                                <!-- Add more sub nav items here -->
                            </ul>
                        </transition>
                    </div>
                    <!-- Add other nav items with sub nav here -->
                </nav>
                <button
                    class="hidden h-8 w-8 p-1 bg-gray-100 text-ash-450 rounded-lg mx-auto border border-solid border-gray-200 hover:border-gray-300"
                    @click="toggleSize">
                    <span v-html="isEnlarge ? enlarge.decrease : enlarge.enlarge"></span>
                </button>
            </header>
        </div>
    </div>
</template>

<style>
.smoothShow {
    width: 300px;
    transition: width 1.5s ease-in-out;
}

.large-menu {
    width: 275px;
    transition: width 0.6s ease-in-out;
}

.small-menu {
    width: 100px;
    transition: width 0.6s ease-in-out;
}

.dropdown-enter-active,
.dropdown-leave-active {
    transition: opacity 0.2s;
}

.dropdown-enter,
.dropdown-leave-to {
    opacity: 0;
}

.pos-r {
    position: relative;
}

.h-screen {
    height: 100vh;
}

.inline-flex {
    display: inline-flex;
}

.flex-col {
    flex-direction: column;
}

.justify-between {
    justify-content: space-between;
}

.bg-white {
    background-color: #fff;
}

.shadow {
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.p-6 {
    padding: 1.5rem;
}

.space-y-2 {
    margin-bottom: 0.5rem;
}

.flex {
    display: flex;
}

.items-center {
    align-items: center;
}

.py-2 {
    padding-top: 0.5rem;
    padding-bottom: 0.5rem;
}

.cursor-pointer {
    cursor: pointer;
}

.hover\:bg-gray-100 {
    --hover-bg-color: #f3f4f6;
}

.hover\:bg-gray-100:hover {
    background-color: var(--hover-bg-color);
}

.bg-indigo-100 {
    background-color: #eef2ff;
}


.pl-2 {
    padding-left: 0.5rem;
}

.pr-6 {
    padding-right: 1.5rem;
}

.rounded-lg {
    border-radius: 0.5rem;
}

.px-2 {
    padding-left: 0.5rem;
    padding-right: 0.5rem;
}

/* .rounded-lg {
    border-radius: 9999px;
} */

.border {
    border-style: solid;
}

.border-solid {
    border-style: solid;
}

.border-gray-200 {
    border-color: #e5e7eb;
}

.hover\:border-gray-300 {
    --hover-border-color: #cbd5e0;
}

.hover\:border-gray-300:hover {
    border-color: var(--hover-border-color);
}

.h-8 {
    height: 2rem;
}

.w-8 {
    width: 2rem;
}

.p-1 {
    padding: 0.25rem;
}

.bg-gray-100 {
    background-color: #f3f4f6;
}


.mx-auto {
    margin-left: auto;
    margin-right: auto;
}

.dropdown-enter-active,
.dropdown-leave-active {
    transition: all 0.8s;
}

.dropdown-enter,
.dropdown-leave-to {
    opacity: 0;
    transform: translateY(-10px);
}
</style>