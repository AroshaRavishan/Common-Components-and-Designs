<script setup>

import FloatingInput from '../../WebCommoncomponents/FloatingInput.vue';
import SelectDropdown from '../../WebCommoncomponents/SelectDropdown.vue';

const selectOptions = [
    { value: '1', label: 'Option 1' },
    { value: '2', label: 'Option 2' },
    { value: '3', label: 'Option 3' },
]
</script>

<template>
    <form class="mt-2">
        <!-- Import Common Compoennts -->
        <FloatingInput id="custom-input" label="Floating Input" placeholder="" />
        <SelectDropdown id="custom-select" label="Custom Select Label" :options="selectOptions" />
    </form>
</template>
