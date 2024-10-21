<template>
  <div>
    <h2>Calculate which product you need</h2>
    <div class="red-retangle" />
    <div class="mt-[64px] flex flex-col">
      <Form @calculate="isCalculation" />
      <div v-if="isCalculate">
        <CalculationResults :data="isCalculate" />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const isCalculate = ref()
const isCalculation = (value: any) => {
  console.log(value)
  isCalculate.value = value
}
</script>

<style scoped></style>