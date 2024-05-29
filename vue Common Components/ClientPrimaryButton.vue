<script setup>
defineProps({
    type: {
        type: String,
        default: 'submit',
    },
    btnClass: {
        type: String,
    },
});
</script>

<template>
    <button :type="type" :class="btnClass ? btnClass:'whitespace-nowrap gap-3 flex items-center text-white font-medium py-2 px-8 border border-primary bg-primary rounded-1 text-base'">
        <slot />
    </button>
</template>
