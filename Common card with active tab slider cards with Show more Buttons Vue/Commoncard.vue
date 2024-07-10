<script setup>
import { computed } from 'vue'
import { usePage } from '@inertiajs/vue3'

const props = defineProps({
    card: {
        type: Object,
        required: true
    }
})

const arrowImageSrc = computed(() => {
    return usePage().props.assetURL ?
        usePage().props.assetURL + '/web-assets/Arrow-Up.svg' :
        '../../web-assets/Arrow-Up.svg'
})
</script>

<template>
    <div class="bg-white rounded-4 shadow-gel-shadow w-full p-5 course-card">
        <img loading="lazy" :src="card.image" alt="course-card-img">
        <h4 class="text-xl sm:text-2xl font-bold text-black-500 h-16 overflow-hidden mt-5 title-line-clamp">{{ card.title }}</h4>
        <p class="text-sm sm:text-base font-normal text-ash-1200 mt-6 h-12 overflow-hidden title-line-clamp">{{ card.subtitle }}</p>
        <p v-if="card.monthlyPayemnt" class="mt-7 text-base sm:text-lg font-semibold text-ash-1200 border-b border-ash-350 pb-1 sm:pb-2 w-max">
            From<span class="text-xl sm:text-2xl text-black-900 font-extrabold mx-1.5">{{ card.monthlyPayemnt }}</span>/ month
        </p>
        <div class="grid md:flex justify-between items-center mt-1 ">
            <div v-if="card.fullPayment">
                <p class="text-base sm:text-lg font-semibold text-black-500">
                    {{ card.fullPayment }}
                    <span v-if="card.cutPrice" class="mx-1.5 text-base sm:text-lg font-semibold text-ash-450 line-through">{{ card.cutPrice }}</span>
                    in full
                </p>
            </div>
            <div class="mt-1.5 md:mt-0">
                <a href="#" class="flex items-center gap-2">
                    <p class="text-base sm:text-lg font-semibold text-black-900">View Details</p>
                    <img loading="lazy" :src="arrowImageSrc" alt="svg-arrow" class="">
                </a>
            </div>
        </div>
    </div>
</template>