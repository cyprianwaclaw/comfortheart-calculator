<template>
    <div class="mt-[100px] mb-[120px]">
        <h3 class="text-[30px]">Usage calculation</h3>
        <div class="red-retangle" />
        <div class="w-[400px] mt-[42px] mb-[64px]">
            <div class="flex justify-between h-[60px] place-items-center bg-[#F5F5F5] px-[21px] rounded-t-md">
                <p class="roboto text-[18px] font-medium text-[#565F5D]">Annual year consumption</p>
                <p class="roboto text-[18px] font-normal text-[#565F5D]">{{ year }}W</p>
            </div>
            <div class="flex justify-between h-[60px] place-items-center bg-[#E4E4E4] px-[21px]">
                <p class="roboto text-[18px] font-medium text-[#565F5D]">Daily usage costs</p>
                <p class="roboto text-[18px] font-normal text-[#565F5D]">${{ daily }}</p>
            </div>
            <div class="flex justify-between h-[60px] place-items-center bg-[#F5F5F5] px-[21px] rounded-b-md">
                <p class="roboto text-[18px] font-medium text-[#565F5D]">Annual usage costs</p>
                <p class="roboto text-[18px] font-normal text-[#565F5D]">${{ cost }}W</p>
            </div>
        </div>
        <h3 class="text-[30px]">Check out our recommended<br> products for your needs</h3>
        <div class="red-retangle" />
        <div class="w-[680px] h-[400px] bg-[#F5F5F5] mt-[52px]">
sa
        </div>
    </div>
</template>

<script setup lang="ts">
const props = defineProps<{
    data: any[];
}>()

const year = ref(1887.5)
const daily = ref(2)
const cost = ref(1887.5)
</script>

<style scoped></style>