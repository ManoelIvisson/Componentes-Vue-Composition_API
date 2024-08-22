<script setup>
  const props = defineProps({
    tipo: {type: String, required: true}
  })

</script>

<template>
  <div class="alerta">
    <p><slot></slot></p>
    <button>x</button>
  </div>
</template>