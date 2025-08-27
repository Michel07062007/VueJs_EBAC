// setup atributo especial feito para manipular o escript
<script setup>
import { reactive } from 'vue';

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

// let contador = 0
const estado = reactive({
  contador: 0,
  email: '',
});

function incrementar() {
  estado.contador++;
}

function decrementar() {
  estado.contador--;
}

function alterarEmail(evento) {
  estado.email =evento => estado.email = evento.target.value;
}
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

  <br/>
  <hr/>

  {{ estado.contador }}
  
  <button @click="incrementar" type="button"></button>
  <button @click="decrementar" type="button"></button>

  
  <br/>
  <hr/>

  {{ estado.email }}
  <input type="email" @keyup="alteraEmail">
</template>


// scoped mostra que sera apenas utilizado aqui, não vaza para outros arquivos
<style scoped>

img { 
  max-width: 200px;
}

</style>
