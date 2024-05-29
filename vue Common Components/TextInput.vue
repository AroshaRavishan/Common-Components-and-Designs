<script setup>
import { onMounted, ref } from 'vue';

defineProps({
    modelValue: String,
    customClass: String
});

defineEmits(['update:modelValue']);

const input = ref(null);

onMounted(() => {
    if (input.value.hasAttribute('autofocus')) {
        input.value.focus();
    }
});

defineExpose({ focus: () => input.value.focus() });
</script>

<template>
    <input type="text"
           ref="input"
           :class="customClass ? customClass: 'dark:bg-gray-950 dark:placeholder:text-white/80 normal-case dark:text-white/80 leading-5.4 ease-soft block w-full appearance-none rounded-2 border border-solid border-ash-350 bg-white bg-clip-padding px-3 py-2.5 font-normal text-ash-1200 outline-none transition-all placeholder:text-ash-1200 focus:border-primary focus:outline-none'"
           :value="modelValue"
           :min="0"
           @keydown.enter.prevent
           @input="$emit('update:modelValue', $event.target.value)"
    />
</template>

<style scoped>
[type="text"], [type="email"], [type="url"], [type="password"], [type="number"], [type="date"], [type="datetime-local"], [type="month"], [type="search"], [type="tel"], [type="time"], [type="week"], [multiple], textarea, select{
    font-size: 14px !important;
    --tw-ring-color: none !important;
}
</style>
