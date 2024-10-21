<template>
    <div class="flex flex-col">
        <label>{{ label }}</label>
        <div class="relative w-[200px]">
            <input v-model="internalValue" @focus="isFocused = true" @blur="handleBlur" :placeholder="placeholder" />
            <Icon name="fluent:chevron-down-16-regular"
                :class="['text-[#828282]', 'absolute', 'right-[11px]', 'top-[11px]', isFocused ? 'rotate-180' : 'rotate-0']"
                size="22" />
            <div v-if="isFocused" class="absolute w-full bg-white border border-gray-300 rounded mt-1 z-10">
                <ul class="option-list">
                    <li v-for="(option, index) in options" :key="index" @click="selectOption(option)"
                        :class="{ 'bg-[#f0f0f0]': internalValue === option, 'hover:bg-gray-200': internalValue !== option }"
                        class="px-4 py-2 cursor-pointer transition-colors duration-200">
                        {{ option }}
                    </li>
                </ul>
            </div>
        </div>
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
const options = ref([
    "Living Room",
    "Bedroom",
    "Hallway / Corridor",
    "Kitchen",
    "Children's room",
    "Bathroom",
    "Restroom",
    "Office",
    "Basement",
    "Attic",
    "Hobby room"
]);

const selectOption = (option: string) => {
    internalValue.value = option
    emit('update:modelValue', option) 
    isFocused.value = false
}

const handleBlur = () => {
    setTimeout(() => {
        isFocused.value = false
    }, 100)
}

watch(() => props.modelValue, (newValue) => {
    internalValue.value = newValue
})
</script>

<style scoped>
.rotate-180 {
    transform: rotate(180deg);
    transition: transform 0.3s ease;
}

.rotate-0 {
    transform: rotate(0deg);
    transition: transform 0.3s ease;
}

.option-list {
    list-style: none;
    padding: 0;
    margin: 0;
    box-shadow: -2px 4px 4px rgba(0, 0, 0, 0.12);
    z-index: 10;
}

.option-list li {
    padding: 8px 16px;
    cursor: pointer;
}

.option-list li:hover {
    background-color: #f0f0f0;
}
</style>