<template>
  <div >
    <input type="number" v-model="estado.num1">
    <input type="number" v-model="estado.num2">
    <select @change="atualizarOperacao" v-model="estado.operacao">
      <option value="">Esolha a operação</option>
      <option value="adicao">Adição</option>
      <option value="subtracao">Subtração</option>
      <option value="multiplicacao">Multiplicação</option>
      <option value="divisao">Divisão</option>
    </select>
    <p>Resultado: {{ operacaoSelect() }}</p>
  </div>
</template>

<script setup>
import { reactive } from 'vue';

const estado = reactive({
  operacao: 'adicao',
  num1: 0,
  num2: 0,
});

const operacaoSelect = () => {
  const { operacao, num1, num2 } = estado;
  switch (operacao) {
    case 'adicao':
      return num1 + num2;
    case 'subtracao':
      return num1 - num2;
    case 'multiplicacao':
      return num1 * num2;
    case 'divisao':
      return num1 / num2;
    default:
      return 0;
  }
};

const atualizarOperacao = (event) => {
  estado.operacao = event.target.value;
};
</script>

<style scoped>

</style>
