<script setup>
  import { ref } from 'vue'
  import CoffePlan from './CoffePlan.vue'

  const plans = ref(["O Único", "O Mais Curioso", "O Mais Viciante"])
  const selectedCoffeePlan = ref('')

  function handleSelectedCoffeePlan(name) {
    selectedCoffeePlan.value = name
  }
</script>

<template>
  {{ selectedCoffeePlan }}
  <div class="plans">
    <coffe-plan v-for="plan in plans" :key="plan" :name="plan" :selected="plan === selectedCoffeePlan"  @selected="handleSelectedCoffeePlan"/>
  </div>
</template>