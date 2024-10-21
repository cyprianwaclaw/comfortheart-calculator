<template>
  <div class="ml-20">
    <h2>Calculate which product you need</h2>
    <div class="red-retangle" />
    <div class="mt-[64px] flex gap-10">
      <Form @calculate="isCalculation" />
    </div>
  </div>
</template>

<script setup>


const isCalculation = (value) => {
  console.log(value)
}
</script>

<style scoped></style>