<script setup>
import { defineProps } from 'vue'

const props = defineProps({
    id: {
        type: String,
        required: true
    },
    label: {
        type: String,
        required: true
    },
    placeholder: {
        type: String,
        default: ''
    }
})
</script>

<template>
    <div class="relative">
        <input type="text" :id="id"
            class="block px-2.5 pb-2.5 pt-4 w-full text-sm text-gray-900 bg-transparent rounded-lg border border-ash-750 appearance-none focus:outline-none focus:ring-0 focus:border-primary-light peer"
            :placeholder="placeholder" />
        <label :for="id"
            class="absolute text-sm text-gray-500 duration-300 transform -translate-y-4 scale-75 top-2 z-10 origin-[0] bg-white px-2 peer-focus:px-2 peer-focus:text-primary-light peer-placeholder-shown:scale-100 peer-placeholder-shown:-translate-y-1/2 peer-placeholder-shown:top-1/2 peer-focus:top-2 peer-focus:scale-75 peer-focus:-translate-y-4 left-1">
            {{ label }}
        </label>
    </div>
</template>