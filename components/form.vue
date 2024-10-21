<template>
    <div>
        <div class="flex gap-[21px] flex-col" @click="error = false">
            <div v-for="(inputPair, index) in inputsArray" :key="inputPair.id" class="flex gap-[19px] place-items-end">
                <InputOptions v-model="inputPair.selectedOption" placeholder="Room" label="Select room" />
                <InputBase v-model="inputPair.selectedBase" placeholder="Size" label="Size" />
                <button v-if="inputsArray.length > 1" class="button-delete" @click="deleteRoom(index)">Delete</button>
                <p v-if="inputsArray.length > 1 && inputsArray.length != index + 1 || isCalculate"
                    class="text-[18px] font-semibold text-[#565F5D] mb-1.5 roboto ml-[32px]">Required power: <span
                        class="font-normal">{{ inputPair.power }}W</span></p>
            </div>
        </div>
        <p v-if="error" class="flex mt-[21px] -mb-[32px] roboto text-[13px] text-[#F21A1A]">Uzupełnij wszytkie pola</p>
        <div class="flex mt-[44px] gap-[14px]">
            <button class="button-primary" @click="addRoom">Add room</button>
            <button class="button-primary" @click="calculate">Calculate</button>
        </div>
    </div>
</template>

<script setup lang="ts">
const emit = defineEmits(['calculate'])
const inputsArray = ref([
    { id: Date.now(), selectedOption: '', selectedBase: '', power: 0 }
])
const isCalculate = ref(false)
const error = ref(false)

const addRoom = () => {
    inputsArray.value.forEach(element => {
        if (!element.selectedOption || !element.selectedBase) {
            error.value = true
        }
    })
    if (!error.value) {
        if (isCalculate.value) {
            emit('calculate', false)
        }
         isCalculate.value = false
        const calculatePower = Number(inputsArray.value[inputsArray.value.length - 1].selectedBase) * 2.5 * 27
        inputsArray.value[inputsArray.value.length - 1].power = calculatePower

        inputsArray.value.push({
            id: Date.now(),
            selectedOption: '',
            selectedBase: '',
            power: null
        })
    }
}

const deleteRoom = (index: number) => {
    inputsArray.value.splice(index, 1)
}

const calculate = () => {

    inputsArray.value.forEach(element => {
        if (!element.selectedOption || !element.selectedBase) {
            error.value = true
        }
    })
    if (!error.value) {
        isCalculate.value = true
        const calculatePower = Number(inputsArray.value[inputsArray.value.length - 1].selectedBase) * 2.5 * 27
        inputsArray.value[inputsArray.value.length - 1].power = calculatePower
        emit('calculate', inputsArray.value)
    }
}
</script>

<style scoped>
.flex {
    display: flex;
}
</style>