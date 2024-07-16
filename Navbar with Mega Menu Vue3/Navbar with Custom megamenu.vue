<script setup>
import {
    ref,
    onMounted
} from 'vue';
import { usePage } from '@inertiajs/vue3'

const isDrawerOpen = ref(false);

const toggleDrawer = () => {
    isDrawerOpen.value = !isDrawerOpen.value;
};

const closeMobileMenu = () => {
    isDrawerOpen.value = false;
};

const handleMouseLeave = () => {
    document.querySelector('.background-overlay').style.opacity = '0';
    const megaMenu = document.querySelector('.mega-menu');
    if (megaMenu) {
        // megaMenu.style.opacity = '0';
        // megaMenu.style.visibility = 'hidden';
        // megaMenu.style.zIndex = '-900';
        megaMenu.style.opacity = '1';
        megaMenu.style.visibility = 'visible';
        megaMenu.style.zIndex = '900';
    }
};

const handleMouseEnter = () => {
    document.querySelector('.background-overlay').style.opacity = '1';
    const megaMenu = document.querySelector('.mega-menu');
    if (megaMenu) {
        megaMenu.style.opacity = '1';
        megaMenu.style.visibility = 'visible';
        megaMenu.style.zIndex = '900';
    }
};

onMounted(() => {
    initFlowbite();
});

const activeCategory = ref(0) // Initialize with the first category
const activeSubcategory = ref(0) // Initialize with the first subcategory

const categories = ref([
    {
        name: 'Business Administration',
        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/administarion.svg' : '../../web-assets/WebRevamp/administarion.svg',
        description: 'Lorem ipsum dolor sit amet consectetur adipiscing elit Ut et elit consectetur adipiscing elit ipsum dolor.',
        subcategories: [
            {
                name: 'PRINCE2® Project Management',
                description: 'Lorem ipsum dolor sit amet consectetur adipiscing elit Ut et elit consectetur adipiscing elit ipsum dolor.',
                courses: [
                    {
                        name: 'PRINCE2® 7 Practitioner Ultimate Edition',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'PRINCE2® 7 Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'PRINCE2® 7 Practitioner',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'PRINCE2® 7 Foundation and Practitioner',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    }
                ]
            },
            {
                name: 'PRINCE2 AGILE',
                description: 'Lorem ipsum dolor sit amet consectetur adipiscing elit Ut et elit consectetur adipiscing elit ipsum dolor2.',
                courses: [
                    {
                        name: 'PRINCE2 Agile® Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'PRINCE2 Agile® Practitioner',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'PRINCE2 Agile® Foundation and Practitioner',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    }
                ]
            },
            {
                name: 'APMG International',
                description: 'Lorem ipsum dolor sit amet consectetur adipiscing elit Ut et elit consectetur adipiscing elit ipsum dolor32.',
                courses: [
                    {
                        name: 'Change Management Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'Change Management Practitioner',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'AgilePM® Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    }
                ]
            },
            {
                name: 'Lean Six Sigma',
                description: 'Lorem ipsum dolor sit amet consectetur adipiscing elit Ut et elit consectetur adipiscing elit ipsum dolor2.',
                courses: [
                    {
                        name: 'PRINCE2 Agile® Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'PRINCE2 Agile® Practitioner',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'PRINCE2 Agile® Foundation and Practitioner',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    }
                ]
            },
            {
                name: 'MSP',
                description: 'Lorem ipsum dolor sit amet consectetur adipiscing elit Ut et elit consectetur adipiscing elit ipsum dolor32.',
                courses: [
                    {
                        name: 'Change Management Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'Change Management Practitioner',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'AgilePM® Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    }
                ]
            }
        ]
    },
    {
        name: 'Finance & Economics',
        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/Finance.svg' : '../../web-assets/WebRevamp/Finance.svg',
        description: 'Lorem ipsum dolor sit amet consectetur adipiscing elit Ut et elit consectetur adipiscing elit ipsum dolor pacaya.',
        subcategories: [
            {
                name: 'Financial Management',
                description: 'Courses focused on financial planning and analysis.',
                courses: [
                    {
                        name: 'Financial Planning and Analysis',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'Corporate Finance',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'Investment Management',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    }
                ]
            },
            {
                name: 'Economics',
                description: 'Courses covering micro and macroeconomics principles.',
                courses: [
                    {
                        name: 'Microeconomics',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'Macroeconomics',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'International Economics',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    }
                ]
            }
        ]
    },
    {
        name: 'Heath & Care',
        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/health.svg' : '../../web-assets/WebRevamp/health.svg',
        description:'Lorem ipsum dolor sit amet consectetur adipiscing elit Ut et elit consectetur adipiscing elit ipsum dolor pacaya.',
        subcategories: [{
                name: 'Graphic Design',
                courses: [
                    {
                        name: 'Change Management Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'Change Management Practitioner',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'AgilePM® Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    }
                ]
            },
            {
                name: 'UX/UI Design',
                courses: [
                    {
                        name: 'Change Management Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'Change Management Practitioner',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'AgilePM® Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    }
                ]
            }
        ]
    },
    {
        name: 'Human Resource Development',
        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/hr.svg' : '../../web-assets/WebRevamp/hr.svg',
        description:'Lorem ipsum dolor sit amet consectetur adipiscing elit Ut et elit consectetur adipiscing elit ipsum dolor pacaya.',
        subcategories: [{
                name: 'Graphic Design',
                courses: [
                    {
                        name: 'Change Management Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'Change Management Practitioner',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'AgilePM® Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    }
                ]
            },
            {
                name: 'UX/UI Design',
                courses: [
                    {
                        name: 'Change Management Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'Change Management Practitioner',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'AgilePM® Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    }
                ]
            }
        ]
    },
    {
        name: 'Information & Technology',
        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/it.svg' : '../../web-assets/WebRevamp/it.svg',
        description:'Lorem ipsum dolor sit amet consectetur adipiscing elit Ut et elit consectetur adipiscing elit ipsum dolor pacaya.',
        subcategories: [{
                name: 'Graphic Design',
                courses: [
                    {
                        name: 'Change Management Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'Change Management Practitioner',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'AgilePM® Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    }
                ]
            },
            {
                name: 'UX/UI Design',
                courses: [
                    {
                        name: 'Change Management Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'Change Management Practitioner',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'AgilePM® Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    }
                ]
            }
        ]
    },
    {
        name: 'Project Management',
        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/projectManagement.svg' : '../../web-assets/WebRevamp/projectManagement.svg',
        description:'Lorem ipsum dolor sit amet consectetur adipiscing elit Ut et elit consectetur adipiscing elit ipsum dolor pacaya.',
        subcategories: [{
                name: 'Graphic Design',
                courses: [
                    {
                        name: 'Change Management Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'Change Management Practitioner',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'AgilePM® Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    }
                ]
            },
            {
                name: 'UX/UI Design',
                courses: [
                    {
                        name: 'Change Management Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'Change Management Practitioner',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'AgilePM® Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    }
                ]
            }
        ]
    },
    {
        name: 'Life Learning',
        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/LifeLearning.svg' : '../../web-assets/WebRevamp/LifeLearning.svg',
        description:'Lorem ipsum dolor sit amet consectetur adipiscing elit Ut et elit consectetur adipiscing elit ipsum dolor pacaya.',
        subcategories: [{
                name: 'Graphic Design',
                courses: [
                    {
                        name: 'Change Management Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'Change Management Practitioner',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'AgilePM® Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    }
                ]
            },
            {
                name: 'UX/UI Design',
                courses: [
                    {
                        name: 'Change Management Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'Change Management Practitioner',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'AgilePM® Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    }
                ]
            }
        ]
    },
    {
        name: 'Teaching & Development',
        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/teaching.svg' : '../../web-assets/WebRevamp/teaching.svg',
        description:'Lorem ipsum dolor sit amet consectetur adipiscing elit Ut et elit consectetur adipiscing elit ipsum dolor pacaya.',
        subcategories: [{
                name: 'Graphic Design',
                courses: [
                    {
                        name: 'Change Management Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'Change Management Practitioner',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'AgilePM® Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    }
                ]
            },
            {
                name: 'UX/UI Design',
                courses: [
                    {
                        name: 'Change Management Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'Change Management Practitioner',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'AgilePM® Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    }
                ]
            }
        ]
    },
    {
        name: 'Other Courses',
        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/other.svg' : '../../web-assets/WebRevamp/other.svg',
        description:'Lorem ipsum dolor sit amet consectetur adipiscing elit Ut et elit consectetur adipiscing elit ipsum dolor pacaya.',
        subcategories: [{
                name: 'Graphic Design',
                courses: [
                    {
                        name: 'Change Management Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'Change Management Practitioner',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'AgilePM® Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    }
                ]
            },
            {
                name: 'UX/UI Design',
                courses: [
                    {
                        name: 'Change Management Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'Change Management Practitioner',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    },
                    {
                        name: 'AgilePM® Foundation',
                        image: usePage().props.assetURL ? usePage().props.assetURL + '/web-assets/WebRevamp/awardingbody-image.svg' : '../../web-assets/WebRevamp/awardingbody-image.svg',
                    }
                ]
            }
        ]
    },
    // Add more main categories here
])


const setActiveCategory = (index) => {
    activeCategory.value = index
    activeSubcategory.value = 0 // Reset to first subcategory when changing main category
}

const setActiveSubcategory = (index) => {
    activeSubcategory.value = index
}

// This ensures that the component is fully initialized before we try to access the categories
onMounted(() => {
    if (categories.value.length > 0 && categories.value[0].subcategories.length > 0) {
        activeCategory.value = 0
        activeSubcategory.value = 0
    }
})

const activeTab = ref(null);

</script>

<template>
    <nav class="bg-beige-300 py-4 sticky w-full top-0 z-10">
        <div class="container flex items-center justify-between">
            <div class="flex-shrink-0 flex gap-6 xl:gap-14 items-center">
                <img loading="lazy" :src="$page.props.assetURL ? $page.props.assetURL + '/web-assets/GelLogo.svg' : '../../web-assets/GelLogo.svg'" alt="GelLogo" class="w-[180px]">
                <div class="hidden lg:block">
                    <div class="hoverable">
                        <!-- Mega menu Button -->
                        <button class="text-black-900 text-base font-bold flex items-center gap-1 py-4" @mouseleave="handleMouseLeave" @mouseenter="handleMouseEnter">Explore Courses
                            <img loading="lazy" :src="$page.props.assetURL ? $page.props.assetURL + '/web-assets/WebRevamp/arrowdown.svg' : '../../web-assets/WebRevamp/arrowdown.svg'" alt="arrowdown" class="">
                        </button>
                        <!-- Mega menu -->
                        <div class="mega-menu">
                            <div @mouseleave="handleMouseLeave" @mouseenter="handleMouseEnter" class="container">
                                <div class=" bg-white sm:shadow-md p-6 dark:bg-neutral-800 sm:dark:border dark:border-neutral-700 dark:divide-neutral-700 mx-auto border border-ash-550 z-1 relative">
                                    <div class="">
                                        <h4 class="text-xl font-semibold text-ash-650 border-b border-ash-1500 pb-4">By Your Goals</h4>
                                    </div>
                                    <div class="static">
                                        <div class="py-0 w-full flex items-center flex-wrap justify-between border-b border-ash-1500">
                                            <div class="flex items-center gap-2 py-5 px-2.5 inline-flex cursor-pointer transition-all duration-300 rounded-2" :class="{ 'bg-primary-light': activeTab === 0 }" @mouseover="activeTab = 0" @mouseleave="activeTab = null">
                                                <div>
                                                    <img loading="lazy" :src="$page.props.assetURL ? $page.props.assetURL + '/web-assets/WebRevamp/awarding.svg' : '../../web-assets/WebRevamp/awarding.svg'" alt="Awarding Bodies" class="max-w-8 max-h-8">
                                                </div>
                                                <h6 class="text-lg font-medium" :class="activeTab === 0 ? 'text-ash-900' : 'text-ash-650'">
                                                    Awarding Bodies
                                                </h6>
                                            </div>
    
                                            <div class="flex items-center gap-2 py-5 px-2.5 inline-flex cursor-pointer transition-all duration-300 rounded-2" :class="{ 'bg-primary-light': activeTab === 1 }" @mouseover="activeTab = 1" @mouseleave="activeTab = null">
                                                <div>
                                                    <img loading="lazy" :src="$page.props.assetURL ? $page.props.assetURL + '/web-assets/WebRevamp/certified.svg' : '../../web-assets/WebRevamp/certified.svg'" alt="Get Certified" class="max-w-8 max-h-8">
                                                </div>
                                                <h6 class="text-lg font-medium" :class="activeTab === 1 ? 'text-ash-900' : 'text-ash-650'">
                                                    Get Certified
                                                </h6>
                                            </div>
    
                                            <div class="flex items-center gap-2 py-5 px-2.5 inline-flex cursor-pointer transition-all duration-300 rounded-2" :class="{ 'bg-primary-light': activeTab === 2 }" @mouseover="activeTab = 2" @mouseleave="activeTab = null">
                                                <div>
                                                    <img loading="lazy" :src="$page.props.assetURL ? $page.props.assetURL + '/web-assets/WebRevamp/online.svg' : '../../web-assets/WebRevamp/online.svg'" alt="Live Online Courses" class="max-w-8 max-h-8">
                                                </div>
                                                <h6 class="text-lg font-medium" :class="activeTab === 2 ? 'text-ash-900' : 'text-ash-650'">
                                                    Live Online Courses
                                                </h6>
                                            </div>
    
                                            <div class="flex items-center gap-2 py-5 px-2.5 inline-flex cursor-pointer transition-all duration-300 rounded-2" :class="{ 'bg-primary-light': activeTab === 3 }" @mouseover="activeTab = 3" @mouseleave="activeTab = null">
                                                <div>
                                                    <img loading="lazy" :src="$page.props.assetURL ? $page.props.assetURL + '/web-assets/WebRevamp/path.svg' : '../../web-assets/WebRevamp/path.svg'" alt="Find Your Career Path" class="max-w-8 max-h-8">
                                                </div>
                                                <h6 class="text-lg font-medium" :class="activeTab === 3 ? 'text-ash-900' : 'text-ash-650'">
                                                    Find Your Career Path
                                                </h6>
                                            </div>
    
                                            <div class="flex items-center gap-2 py-5 px-2.5 inline-flex cursor-pointer transition-all duration-300 rounded-2" :class="{ 'bg-primary-light': activeTab === 4 }" @mouseover="activeTab = 4" @mouseleave="activeTab = null">
                                                <div>
                                                    <img loading="lazy" :src="$page.props.assetURL ? $page.props.assetURL + '/web-assets/WebRevamp/resources.svg' : '../../web-assets/WebRevamp/resources.svg'" alt="Free Resources" class="max-w-8 max-h-8">
                                                </div>
                                                <h6 class="text-lg font-medium" :class="activeTab === 4 ? 'text-ash-900' : 'text-ash-650'">
                                                    Free Resources
                                                </h6>
                                            </div>
                                        </div>
                                        <div class="">
                                            <!-- Sample data divs -->
                                            <div v-if="activeTab === 0" class="p-4" @mouseover="activeTab = 0" @mouseleave="activeTab = null">
                                                <h3 class="text-xl font-bold mb-2">Awarding Bodies</h3>
                                                <p>Hi! We partner with top institutions such as:</p>
                                                <ul class="list-disc pl-5 mt-2">
                                                    <li>International Association of Project Managers (IAPM)</li>
                                                    <li>Chartered Institute of Marketing (CIM)</li>
                                                    <li>Association for Project Management (APM)</li>
                                                </ul>
                                            </div>
    
                                            <div v-if="activeTab === 1" class="p-4" @mouseover="activeTab = 1" @mouseleave="activeTab = null">
                                                <h3 class="text-xl font-bold mb-2">Get Certified</h3>
                                                <p>Hi! Boost your career with our certifications:</p>
                                                <ul class="list-disc pl-5 mt-2">
                                                    <li>Project Management Professional (PMP)</li>
                                                    <li>Certified Information Systems Security Professional (CISSP)</li>
                                                    <li>Certified Information Systems Auditor (CISA)</li>
                                                </ul>
                                            </div>
    
                                            <div v-if="activeTab === 2" class="p-4" @mouseover="activeTab = 2" @mouseleave="activeTab = null">
                                                <h3 class="text-xl font-bold mb-2">Live Online Courses</h3>
                                                <p>Hi! Join our interactive online sessions:</p>
                                                <ul class="list-disc pl-5 mt-2">
                                                    <li>Agile Project Management</li>
                                                    <li>Data Science Fundamentals</li>
                                                    <li>Cybersecurity Essentials</li>
                                                </ul>
                                            </div>
    
                                            <div v-if="activeTab === 3" class="p-4" @mouseover="activeTab = 3" @mouseleave="activeTab = null">
                                                <h3 class="text-xl font-bold mb-2">Find Your Career Path</h3>
                                                <p>Hi! Explore these promising career paths:</p>
                                                <ul class="list-disc pl-5 mt-2">
                                                    <li>Cloud Computing Specialist</li>
                                                    <li>Data Analyst</li>
                                                    <li>Digital Marketing Manager</li>
                                                </ul>
                                            </div>
    
                                            <div v-if="activeTab === 4" class="p-4" @mouseover="activeTab = 4" @mouseleave="activeTab = null">
                                                <h3 class="text-xl font-bold mb-2">Free Resources</h3>
                                                <p>Hi! Access our free learning materials:</p>
                                                <ul class="list-disc pl-5 mt-2">
                                                    <li>E-books on Project Management</li>
                                                    <li>Webinars on Digital Marketing Trends</li>
                                                    <li>Practice Tests for IT Certifications</li>
                                                </ul>
                                            </div>
                                        </div>
                                    </div>
                                    <!-- Mega menu Categories -->
                                    <div class="grid grid-cols-1 lg:grid-cols-12 CategoryPanel">
                                        <!-- Left Section -->
                                        <div class="col-span-1 lg:col-span-3 border-r border-ash-1500 pr-6">
                                            <div class="">
                                                <h4 class="text-xl font-semibold text-ash-650 border-b border-ash-1500 py-6">By Topics</h4>
                                            </div>
                                            <div class="pt-6">
                                                <!-- Main Categories Section -->
                                                <ul class="space-y-0 h-[373px] 4xl:h-auto overflow-auto">
                                                    <li v-for="(category, index) in categories" :key="index" class="p-2.5 cursor-pointer transition-colors duration-200 flex gap-2 items-center rounded-2" :class="{ 'bg-ash-850': activeCategory === index, 'hover:bg-gray-100': activeCategory !== index }" @mouseover="setActiveCategory(index)">
                                                        <div class="">
                                                            <img loading="lazy" :src="category.image" alt="image" class="">
                                                        </div>
                                                        <h3 class="text-base font-medium text-ash-650">{{ category.name }}</h3>
                                                    </li>
                                                </ul>
                                            </div>
                                        </div>
                                        <!-- Right Section -->
                                        <div class="col-span-1 lg:col-span-9">
                                            <div class="sm:grid sm:grid-cols-2">
                                                <!-- Subcategories Section -->
                                                <div class="flex flex-col border-r border-ash-1500">
                                                    <div class="flex flex-col pt-6 px-6">
                                                        <h2 class="text-xl font-semibold text-ash-650">{{ categories[activeCategory].name }}</h2>
                                                        <p class="mt-5 text-sm font-normal text-ash-1400">{{ categories[activeCategory].description }}</p>
                                                        <div class="py-4 border-b border-ash-1500">
                                                            <button class="rounded-1 border border-black-500 text-black-500 text-base font-semibold py-2.5 px-12 hover:text-black-500 cursor-pointer">View all</button>
                                                        </div>
                                                        <div class="pt-5">
                                                            <h4 class="text-lg font-semibold text-ash-650">Top Categories</h4>
                                                        </div>
                                                        <ul class="space-y-3 mt-4 h-[200px] 4xl:h-auto overflow-auto">
                                                            <li v-for="(subcategory, index) in categories[activeCategory].subcategories" :key="index" class="cursor-pointer p-2.5 rounded-2 transition-colors duration-200 border border-ash-1500" :class="{ 'bg-beige-300': activeSubcategory === index, 'hover:bg-gray-50': activeSubcategory !== index }" @mouseover="setActiveSubcategory(index)">
                                                                <h3 class="text-base font-medium text-ash-650">{{ subcategory.name }}</h3>
                                                            </li>
                                                        </ul>
                                                    </div>
                                                </div>
                                                <!-- Courses Section -->
                                                <div class="flex flex-col pt-6 px-6">
                                                    <h3 class="text-xl font-semibold text-ash-650">
                                                        {{ categories[activeCategory].subcategories[activeSubcategory].name }} Courses
                                                    </h3>
                                                    <!-- <p class="mt-5 text-sm font-normal text-ash-1400">{{ categories[activeCategory].subcategories[activeSubcategory].description }}</p>
                                                    <div class="py-4 border-b border-ash-1500">
                                                        <button class="rounded-1 border border-black-500 text-black-500 text-base font-semibold py-2.5 px-12 hover:text-black-500 cursor-pointer">View all Courses</button>
                                                    </div>
                                                    <div class="pt-5">
                                                        <h4 class="text-lg font-semibold text-ash-650">Trending Courses</h4>
                                                    </div> -->
                                                    <ul class="sm:grid sm:grid-cols-2 gap-y-6 gap-x-4 mt-7 h-[170px] 4xl:h-auto overflow-auto">
                                                        <li v-for="(course, courseIndex) in categories[activeCategory].subcategories[activeSubcategory].courses" :key="courseIndex" class="flex flex-row rounded-2">
                                                            <div class="hidden">
                                                                <img :src="course.image" alt="Course image" class="max-w-[50px] max-h-[50px]">
                                                            </div>
                                                            <h5 class="text-base font-medium text-ash-650 max-h-[3rem] overflow-hidden title-line-clamp cursor-pointer">
                                                                {{ course.name }}
                                                            </h5>
                                                        </li>
                                                    </ul>
                                                    <button class="mt-7 text-black-900 text-base font-semibold hover:text-black-500 flex gap-2 items-center border-b border-transparent hover:border-b hover:border-black-900 cursor-pointer transition-all duration-300 ease-in-out w-max">
                                                        View all trending courses
                                                        <img loading="lazy" :src="$page.props.assetURL ? $page.props.assetURL + '/web-assets/Arrow-Up.svg' : '../../web-assets/Arrow-Up.svg'" alt="Arrow-Up svg" class="">
                                                    </button>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <div class="absolute inset-0 bg-black-500 bg-opacity-75 transition-opacity h-screen background-overlay"></div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="hidden lg:flex gap-1 xl:gap-6">
                <div class="flex">
                    <ul class="flex space-x-4 items-center">
                        <li>
                            <router-link to="#Corporate" class="text-black-900 text-base font-bold">Corporate Training</router-link>
                        </li>
                        <li>
                            <router-link to="#Instructor" class="text-black-900 text-base font-bold">Become an Instructor</router-link>
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
                <button @click="toggleDrawer" class="block text-black-500 focus:outline-none">
                    <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path v-if="isOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                        <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
                    </svg>
                </button>
            </div>
        </div>

        <!-- Mobile menu Drawer -->
        <transition enter-active-class="transition ease-out duration-300" enter-from-class="opacity-0 translate-x-full" enter-to-class="opacity-100 translate-x-0" leave-active-class="transition ease-in duration-300" leave-from-class="opacity-100 translate-x-0" leave-to-class="opacity-0 translate-x-full">
            <div v-if="isDrawerOpen" class="fixed inset-0 overflow-hidden z-50 block lg:hidden">
                <div class="absolute inset-0 overflow-hidden">
                    <div class="absolute inset-0 bg-gray-500 bg-opacity-75 transition-opacity" @click="toggleDrawer"></div>
                    <section class="absolute inset-y-0 right-0 max-w-full flex">
                        <div class="w-screen">
                            <div class="h-full flex flex-col bg-white shadow-xl overflow-y-scroll">
                                <div class="p-6 flex items-center justify-between">
                                    <h2 class="text-lg font-medium text-gray-900">Explore Courses</h2>
                                    <button @click="toggleDrawer" class="">
                                        <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                                        </svg>
                                    </button>
                                </div>
                                <div class="flex-1 p-6">
                                    <div class="sm:grid sm:grid-cols-1 gap-4">
                                        <div class="flex flex-col">
                                            <a @click="closeMobileMenu" class="flex items-center gap-x-3.5 py-2 px-3 rounded-lg text-sm text-gray-800 hover:bg-gray-100 focus:ring-2 focus:ring-blue-500" href="#">
                                                About
                                            </a>
                                            <a @click="closeMobileMenu" class="flex items-center gap-x-3.5 py-2 px-3 rounded-lg text-sm text-gray-800 hover:bg-gray-100 focus:ring-2 focus:ring-blue-500" href="#">
                                                Services
                                            </a>
                                            <a class="flex items-center gap-x-3.5 py-2 px-3 rounded-lg text-sm text-gray-800 hover:bg-gray-100 focus:ring-2 focus:ring-blue-500" href="#">
                                                Customer Story
                                            </a>
                                        </div>
                                        <div class="flex flex-col">
                                            <a @click="closeMobileMenu" class="flex items-center gap-x-3.5 py-2 px-3 rounded-lg text-sm text-gray-800 hover:bg-gray-100 focus:ring-2 focus:ring-blue-500" href="#">
                                                Log In
                                            </a>
                                            <a @click="closeMobileMenu" class="flex items-center gap-x-3.5 py-2 px-3 rounded-lg text-sm text-gray-800 hover:bg-gray-100 focus:ring-2 focus:ring-blue-500" href="#">
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
        <!-- End Mobile menu Drawer -->
    </nav>
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

.mega-menu {
    opacity: 0;
    visibility: hidden;
    z-index: -900;
    left: 0;
    position: absolute;
    text-align: left;
    width: 100%;
    transition: all 0.15s linear 0s;
}

/* #hoverable Class Styles */
.hoverable {
    position: static;
}

.hoverable>a:after {
    content: "\25BC";
    font-size: 10px;
    padding-left: 6px;
    position: relative;
    top: -1px;
}
</style>