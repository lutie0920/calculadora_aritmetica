<script setup>
import { reactive } from 'vue';

const estado = reactive ({
  operacao: "Escolha a operação",
  n1: 0,
  n2: 0,
})

function operacaoSomar(){
  return parseInt(estado.n1) + parseInt(estado.n2);
}

function operacaoSubtrair(){
  return estado.n1 - estado.n2;
}

function operacaoMultiplicar(){
  return estado.n1 * estado.n2;
}

function operacaoDividir(){
  return estado.n1 / estado.n2;
}

const getOperacao = () =>{
  const {operacao} = estado;

  switch(operacao){
    case 'somar':
      return operacaoSomar();
    case 'subtrair':
      return operacaoSubtrair();
    case 'multiplicar':
      return operacaoMultiplicar();
    case 'dividir':
      return operacaoDividir();
  }
}


</script>

<template>
  <div class="container text-center">
    <header class="p-5">
      <h1>Calculadora Aritimética</h1>
    </header>
    <div class="row justify-content-center">
      <div class="col-6 col-sm-3 mb-3">
        <input type="number" placeholder="Digite o primeiro número" class="form-control" @keyup="evento => estado.n1 = evento.target.value"> 
      </div>
    </div>
    <div class="row justify-content-center">
      <div class="col-6 col-sm-3 mb-3">
        <input type="number" placeholder="Digite o segundo número" class="form-control" @keyup="evento => estado.n2 = evento.target.value"> 
      </div>
    </div>
    <div class="row justify-content-center">
      <div class="col-6 col-sm-3 mb-3">
        <select @change="evento => estado.operacao = evento.target.value" class="form-control">
          <option>Escolha a operação</option>
          <option value="somar">Somar</option>
          <option value="subtrair">Subtrair</option>
          <option value="multiplicar">Multiplicar</option>
          <option value="dividir">Dividir</option>
        </select>
      </div>
    </div>
    <h2>O resultado é {{ getOperacao() }}</h2>
  </div>
</template>

<style scoped>
</style>
