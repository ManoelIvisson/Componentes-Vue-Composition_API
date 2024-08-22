<script setup>
  import { ref, onMounted } from 'vue';

  const props = defineProps({
    nomeUsuario: {type: String, required: true}
  })

  const usuario = ref({})

  async function buscarUsuario() {
    let infoUsuario = await fetch(`https://api.github.com/users/${props.nomeUsuario}`).then(resultado => resultado.json())

    // Divide o nome do usuário e depois seleciona apenas o primeiro nome e o sobrenome
    let nome = infoUsuario.name.split(' ')

    if (nome.length > 1) {
      infoUsuario.name = nome[0] + ' ' + nome[1]
    }

    usuario.value = {
      imagemUsuario: infoUsuario.avatar_url,
      nome: infoUsuario.name,
      seguidores: infoUsuario.followers,
      seguindo: infoUsuario.following,
      url: infoUsuario.html_url
    }
  }

  onMounted(() => {
    buscarUsuario()
  })
</script>

<template>
  <div class="card">
    <div class="imagemUsuario">
      <img :src="usuario.imagemUsuario" alt="">
    </div>

    <div class="infoUsuario">
      <h2>{{ usuario.nome }}</h2>
      <p><span>Seguidores:</span> {{ usuario.seguidores }}</p>
      <p><span>Seguindo:</span> {{ usuario.seguindo }}</p>
      <button>
        <a :href="usuario.url" target="_blank">
          Ver Perfil
        </a>
      </button>
    </div>
  </div>
</template>