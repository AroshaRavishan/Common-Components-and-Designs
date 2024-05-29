<script setup>
defineProps({
    btnClass: String,
    type: {
        type: String,
        default: 'button',
    },
});
</script>

<template>
    <button :type="type" :class="btnClass ? btnClass: 'whitespace-nowrap gap-3 flex items-center text-primary font-medium py-2 px-8 border border-primary bg-white rounded-1 text-base'">
        <slot />
    </button>
</template>
