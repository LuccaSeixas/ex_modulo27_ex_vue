<script setup>
import { reactive } from 'vue';

  const estado = reactive({
    filtro: "+",
    input1: "",
    input2: "",
    resultado: ""
  })

  const getSoma = () => {
    return estado.input1 + estado.input2;
  };

  const getSubtracao = () => {
    return estado.input1 - estado.input2;
  }

  const getDivisao = () => {
    return estado.input1 / estado.input2;

  }

  const getMultiplicacao = () => {
    return estado.input1 * estado.input2;
  }

  const mostraResultado = () => {

    switch (estado.filtro) {
      case '+':
        estado.resultado = getSoma();
        break;
      case '-':
        estado.resultado = getSubtracao();
        break;
      case '/':
        estado.resultado = getDivisao();
        break;
      case 'x':
        estado.resultado = getMultiplicacao();
        break;
      default:
        estado.resultado = "";
    }
  };
</script>

<template>

  <div class="container">
    <form>
      <div class="row mt-5">
        <div class="col-3">
          <input v-model="estado.input1" @input="mostraResultado" type="number" class="form-control no-spinner" placeholder="Adicionar Número">
        </div>
        <div class="col">
          <select v-model="estado.filtro" @change="mostraResultado" class="text-center form-control">
            <option value="+">+</option>
            <option value="-">-</option>
            <option value="/">/</option>
            <option value="x">X</option>
          </select>
        </div>
        <div class="col-3">
          <input v-model="estado.input2" @input="mostraResultado" type="number" class="form-control no-spinner" placeholder="Adicionar Número">
        </div>
        <div class="col text-center p-0 align-self-center">
          <span>=</span>
        </div>
        <div class="col-4">
          <input v-model="estado.resultado" type="number" class="form-control" id="resultado" readonly>
        </div>
      </div>
    </form>
  </div>

</template>

<style scoped>
  .no-spinner::-webkit-outer-spin-button,
  .no-spinner::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }
  .no-spinner {
    -moz-appearance: textfield;
  }
</style>
