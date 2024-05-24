<script setup>
import { onMounted, ref, toRef } from 'vue';
import InputLabel from '@/Components/InputLabel.vue';
import InputError from '@/Components/InputError.vue';
const model = defineModel({
    type: String,
    required: true,
});

const props = defineProps({
    label: {
        type: String,
        default: null,
    },
    id: {
        type: String,
        required: true,
    },
    error: {
        type: String,
        default: null,
    },
    class: {
        type: String,
        default: null,
    },
});

// const { label, id } = toRef(props);

const input = ref(null);

onMounted(() => {
    if (input.value.hasAttribute('autofocus')) {
        input.value.focus();
    }
});

defineExpose({ focus: () => input.value.focus() });
</script>

<template>
    <InputLabel v-if="$props.label" :for="$props.id" :value="$props.label" />
    <input
        class="border-gray-300 dark:border-gray-700 dark:bg-gray-900 dark:text-gray-300 focus:border-indigo-500 dark:focus:border-indigo-600 focus:ring-indigo-500 dark:focus:ring-indigo-600 rounded-md shadow-sm"
        :class="class"
        v-model="model"
        ref="input"
    />
    <InputError class="mt-2" :message="error" />
</template>
