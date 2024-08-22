<script setup>
  import { ref, onMounted, computed } from 'vue'

  const props = defineProps({
    tipo: {type: String, required: true}
  })

  const alertaVisivel = ref(true)

  const propriedadesAlerta = computed(() => {
    if (props.tipo == 'info') {
      return {
        icone: 'info', 
        estilo: 'info'}
    } else if (props.tipo == 'sucesso') {
      return {
        icone: 'check_circle', 
        estilo: 'sucesso'}
    } else if (props.tipo == 'aviso') {
      return {
        icone: 'warning', 
        estilo: 'aviso'}
    } else if (props.tipo == 'erro') {
      return {
        icone: 'error', 
        estilo: 'erro'}
    }
  })

  const emit = defineEmits(['fecharAlerta'])
  
  function fecharAlerta() {
    alertaVisivel.value = false
    emit('fecharAlerta')
  }

</script>

<template>
  <div v-show="alertaVisivel" class="alerta" :class="propriedadesAlerta.estilo">
    <p class="comunicado">
      <span class="material-symbols-outlined">
        {{ propriedadesAlerta.icone }}
      </span> 
      <slot></slot>
    </p>
    <button @click="fecharAlerta">
      <span class="material-symbols-outlined">
        close
      </span>
    </button>
  </div>
</template>