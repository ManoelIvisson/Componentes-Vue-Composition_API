<script setup>
    import { ref } from 'vue'
    import CoffePlan from './CoffePlan.vue'

    const plans = ref(["O Único", "O Mais Curioso", "O Mais Viciante"])
</script>

<template>
    <div class="plans">
        <coffe-plan v-for="plan in plans" :key="plan" :name="plan" />
    </div>
</template>