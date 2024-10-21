<template>
    <div class="flex flex-col">
        <label>{{ label }}</label>
        <input v-model="internalValue" :placeholder="placeholder" @blur="handleBlur" class="w-[100px]" type="number" />
    </div>
</template>

<script setup lang="ts">
const props = defineProps<{
    modelValue: string;
    label: string;
    placeholder: string;
}>()

const emit = defineEmits(['update:modelValue'])
const internalValue = ref(props.modelValue || '')
const isFocused = ref(false)

const handleBlur = () => {
    setTimeout(() => {
        isFocused.value = false
    }, 100)
}

watch(internalValue, (newValue: string) => {
    emit('update:modelValue', newValue)
})
</script>

<style scoped>
input[type=number]::-webkit-inner-spin-button,
input[type=number]::-webkit-outer-spin-button {
    -webkit-appearance: none;
    margin: 0;
}

input[type=number] {
    -moz-appearance: textfield;
}
</style>