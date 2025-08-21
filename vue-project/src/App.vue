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

const botaoEstaDesabilitado = false
</script>

<template>
  <h1>{{ dizOla("Paula") }}</h1>
  <img :src="endereçoDaImagem">

  <button :disable="botaoEstaDesabilitado">Enviar mensagem</button>
</template>


// scoped mostra que sera apenas utilizado aqui, não vaza para outros arquivos
<style scoped>
</style>
