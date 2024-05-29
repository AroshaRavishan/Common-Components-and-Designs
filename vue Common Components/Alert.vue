<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
    section: Object,
    massage: String,
});

const { emit } = defineEmits(['close']);
</script>

<template>
    <div class="bg-primary shade-class border border-primary rounded-1.5 px-4 py-2.5">
        <div class="flex items-center justify-between">
            <div class="flex items-center gap-3">
                <div class="">
                    <svg width="32" height="32" viewBox="0 0 32 32" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
                        <circle cx="16" cy="16" r="15.75" class="!text-primary" fill="" stroke="" stroke-width="0.5" />
                        <path class="!text-primary" d="M16 12.25C15.5875 12.25 15.2344 12.1031 14.9406 11.8094C14.6469 11.5156 14.5 11.1625 14.5 10.75C14.5 10.3375 14.6469 9.98438 14.9406 9.69063C15.2344 9.39687 15.5875 9.25 16 9.25C16.4125 9.25 16.7656 9.39687 17.0594 9.69063C17.3531 9.98438 17.5 10.3375 17.5 10.75C17.5 11.1625 17.3531 11.5156 17.0594 11.8094C16.7656 12.1031 16.4125 12.25 16 12.25ZM16 22.75C15.6875 22.75 15.4219 22.6406 15.2031 22.4219C14.9844 22.2031 14.875 21.9375 14.875 21.625V14.875C14.875 14.5625 14.9844 14.2969 15.2031 14.0781C15.4219 13.8594 15.6875 13.75 16 13.75C16.3125 13.75 16.5781 13.8594 16.7969 14.0781C17.0156 14.2969 17.125 14.5625 17.125 14.875V21.625C17.125 21.9375 17.0156 22.2031 16.7969 22.4219C16.5781 22.6406 16.3125 22.75 16 22.75Z" fill="white" />
                    </svg>
                </div>
                <div class="text-primary font-normal text-base">
                    {{ massage }}
                </div>
            </div>
            <div class="">
                <img src="https://cdn-icons-png.flaticon.com/128/2732/2732657.png" loading="lazy" alt="Close" title="Close" width="20" height="20" @click="emit('close')">
            </div>
        </div>
    </div>
</template>
