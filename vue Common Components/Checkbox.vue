<script setup>
import { computed } from "vue";

const emit = defineEmits(["update:checked"]);

const props = defineProps({
    value: {
        type: String,
        default: null,
    },
    disabled: {
        type: Boolean,
        default: false,
    },
    options: {
        type: Array,
        default: () => [],
    },
    checkType: {
        type: String,
        default: "Multiple",
    },
    selectedItems: {
        type: Array,
        default: () => [],
    },
});

//updaate option
const proxyChecked = computed({
    get() {
        //check options if it is an array
        if (props.checkType === "All" && props.options.length == props.selectedItems.length && props.selectedItems.length > 0) {
            return true;
        } else if (props.checkType === "All" && props.options.length != props.selectedItems.length) {
            return false;
        } else if (Array.isArray(props.options) && props.checkType === "Multiple") {
            return props.options.includes(props.value) ? true : false;
        }
    },

    set(val) {
        emit("update:checked", val);
    },
});

const updateOption = () => {
    emit("update:selection", { value: props.value, checkType: props.checkType });
};
</script>

<template>
    <input
        v-model="proxyChecked"
        type="checkbox"
        :value="value"
        @change="updateOption"
        :disabled="disabled"
        class="w-4 h-4 text-primary bg-gray-100 border-gray-300 rounded focus:ring-primary dark:focus:ring-primary dark:ring-offset-gray-800 dark:focus:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600"
    />
</template>

