<script setup>
    defineProps({
        name: String,
        price: Number
    })
</script>

<template>
    <div class="plan">
      <div class="description">
        <span class="title"> {{ name }} </span>
      </div>
    </div>
</template>