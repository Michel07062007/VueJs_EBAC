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
  saldo: 5000,
  transferindo: 0,
  nomes: ['gian', 'paulo', 'luisa', 'monica'],
  nomeAInserir: '',
});

function incrementar() {
  estado.contador++;
}

function decrementar() {
  estado.contador--;
}

function mostraSaldoFuturo {
  const { saldo, transferindo } = estado;
  return saldo - transferindo;
}

function calidaValorTransferencia() {
  const { saldo, transferindo } = estado;
  return saldo >= transferindo;
}

function cadastraNome() {
  if (estado.nomeAInserir.length >= 3) {
    estado.nomes.push(estado.nomeAInserir)
  } else {
    alert("Digita mais caracteres")
  }
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

  <br/>
  <hr/>

  saldo: {{ estado.saldo }}
  transferindo: {{ estado.transferindo }}
  Saldo depois da transferencia: {{ mostraSaldoFuturo }}
  <input class="campo" :class="{ invalido: !calidaValorTransferencia() }" @keyup="evento => estado.transferindo = evento.target.value" type="number" placeholder="Quantia para transferir">
  <button v-if="validaValorTransferencia()">transferir</button>
  <span v-else>valor maior que o saldo da conta</span>

  <br/>
  <hr/>

  <ul>
    <li v-for="nome in estado.nomes">
      {{ nome }}
    </li>
  </ul>
  <input @keyup="evento => estado.nomeAInserir = evento.target.value"  type="text" placeholder="Digite um novo nome">
  <button @click="cadastraNome"  type="button">Cadastrar nome</button>

  <h3 v-for="nome in estado.nomes">{{ nome }}</h3>
</template>


// scoped mostra que sera apenas utilizado aqui, não vaza para outros arquivos
<style scoped>

img { 
  max-width: 200px;
}

.invalido {
  outline-color: red;
  border-color: red;
}

.campo {
  border: 2px solid #000;
}
</style>
