<script setup>
  import { ref } from 'vue'

  const props = defineProps({
    name: {type: String, default: 'Default Name', validator(value) {
      return value.startsWith('O')
    }},
    selected: {type: Boolean, default: false}
  })

  const emit = defineEmits({
    selected(payload) {
      return typeof payload === 'string'
    }
  })

  function selectPlan() {
    emit('selected', props.name)
  } 
</script>

<template>
  <div @click="selectPlan" :class="{ 'active-plan': selected }" class="plan">
    <div class="description">
      <span class="title"> {{ name }} </span>
    </div>
  </div>
</template>