// setup atributo especial feito para manipular o escript
<script setup>
const nome = "Michel klein"
const meuObj = {
  nome: "Michel",
  filmeFavorito: "Enigma de outro mundo"
}

function dizOla(nome) {
  return `${nome} diz oi`;
}

const endereçoDaImagem = "https://cdn.pixabay.com/photo/2025/08/11/10/07/milky-way-9767930_1280.jpg"
const imagenAleatoria = "https://cdn.pixabay.com/photo/2025/08/11/10/07/milky-way-9767930_1280.jpg"

const botaoEstaDesabilitado = false

const gostaDoBatman = true
const gostaDoSuperMan = true

const estaAutorizado = false
</script>

<template>
  <h1>{{ dizOla("Paula") }}</h1>
  <img v-if="gostaDoBatman" :src="endereçoDaImagem">
  <img v-else-if="gostaDoSuperMan" :src="imagenAleatoria">
  <h2 v-else>Não curte heróis da DC</h2>

  <h1 v-if="estaAutorizado">Bem-vindo</h1>
  <h2 v-else>Não possui acesso</h2>

  <h1></h1>

  <button :disable="botaoEstaDesabilitado">Enviar mensagem</button>
</template>


// scoped mostra que sera apenas utilizado aqui, não vaza para outros arquivos
<style scoped>

img { 
  max-width: 200px;
}

</style>
