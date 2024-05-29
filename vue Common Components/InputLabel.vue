<script setup>
defineProps({
    value: String,
    customClass: String,
    helpingText: {
        type: String,
        default: ''
    }
});
</script>

<template>
    <label :class="customClass ? customClass: 'inline-block mb-2 ml-0 font-normal text-base text-ash-1200 dark:text-white/80'" style="margin-top: 20px">
        <span v-if="value">{{ value }}
            <span class="text-[8px] font-semibold text-[#ADB5BD]"> {{ helpingText }}</span>
        </span>
        <span v-else><slot /></span>
    </label>
</template>
