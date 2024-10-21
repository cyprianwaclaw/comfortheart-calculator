<template>
    <div>
        <div class="flex gap-[21px] flex-col">
            <div v-for="(inputPair, index) in inputsArray" :key="inputPair.id" class="flex gap-[19px] place-items-end">
                <InputOptions v-model="inputPair.selectedOption" placeholder="Room" label="Select room" />
                <InputBase v-model="inputPair.selectedBase" placeholder="Size" label="Room size" />
                <button v-if="inputsArray.length > 1" class="button-delete" @click="deleteRoom(index)">Delete</button>
            </div>
        </div>
        <div class="flex mt-[44px] gap-[14px]">
            <button class="button-primary" @click="addRoom">Add room</button>
            <button class="button-primary" @click="calculate">Calculate</button>
        </div>
    </div>
</template>

<script setup>

const emit = defineEmits(['calculate'])
const inputsArray = ref([
    { id: Date.now(), selectedOption: '', selectedBase: '' }
])

const addRoom = () => {
    inputsArray.value.push({
        id: Date.now(),
        selectedOption: '',
        selectedBase: ''
    });
}

const deleteRoom = (index) => {
    inputsArray.value.splice(index, 1)
}

const calculate = () => {
    emit('calculate', inputsArray.value)
}
</script>

<style scoped>
.flex {
    display: flex;
}
</style>