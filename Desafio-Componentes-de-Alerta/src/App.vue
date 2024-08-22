<script setup>
  import AppAlerta from './components/AppAlerta.vue'

  function aviso() {
    console.log('Alerta Fechado')
  }
</script>

<template>
  <app-alerta tipo="info" @fechar-alerta="aviso"> Novas opurtunidades de emprego chegaram! </app-alerta>
  <app-alerta tipo="sucesso" @fechar-alerta="aviso"> Parabéns, você foi contratado! </app-alerta>
  <app-alerta tipo="aviso" @fechar-alerta="aviso"> Teste liberado </app-alerta>
  <app-alerta tipo="erro" @fechar-alerta="aviso"> Houve uma falha, tente novamente mais tarde </app-alerta>
</template>

