<script setup>
  import { computed, reactive } from 'vue';

  import Cabecalho from './components/Cabecalho.vue'
  import Calculadora from './components/Calculadora.vue'

const estado = reactive({
  valorInput1: 0,
  valorInput2: 0,
  operacao: "soma",
})

function realizarOperacao(valor1, valor2, operacao) {
  switch (operacao) {
    case "soma":
      return valor1 + valor2;
    case "subtracao":
      return valor1 - valor2;
    case "multiplicacao":
      return valor1 * valor2;
    case "divisao":
      return valor1 / valor2;
    default:
      return 0;
  }
}

const resultadoOperacao = computed(() => {
  const valor1 = parseFloat(estado.valorInput1);
  const valor2 = parseFloat(estado.valorInput2);
  const operacao = estado.operacao;

  return realizarOperacao(valor1, valor2, operacao)
})

const updateNum1 = (evento) => {
  estado.valorInput1 = parseFloat(evento.target.value);
}

const updateNum2 = (evento) => {
  estado.valorInput2 = parseFloat(evento.target.value);
}

const updateCalcular = (evento) => {
  estado.operacao = evento.target.value;
}

</script>

<template>
  <div class="container">
    <Cabecalho />
    <Calculadora :num1="estado.valorInput1" :calcular="estado.operacao" :num2="estado.valorInput2" :resultado-calculo="resultadoOperacao"
      :atualizar-num1="updateNum1" :atualizar-num2="updateNum2" :atualizar-calculo="updateCalcular"/>
  </div>
</template>

<style scoped>

</style>
