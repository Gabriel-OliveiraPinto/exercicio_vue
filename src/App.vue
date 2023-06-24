<script setup>
import { reactive } from 'vue';
  
const estado = reactive({
  operacao: 'soma',
  tarefaTemp: '',
  numero1: 0,
  numero2: 0,
})



const getOperacao = () => {
  const { operacao, numero1, numero2 } = estado;

  switch(operacao) {
    case 'soma': 
      return numero1 + numero2;
    case 'subtrair':
      return numero1 - numero2;
    case 'multiplicar':
      return numero1 * numero2;
    case 'dividir':
      return numero1 / numero2;
  }
  
}

</script>

<template>
  <div class="container">
    <header class="p-5 mb-4mt-4 bg-light rounded-3">
    <h1>Minha Calculadora</h1>
    
    </header>
    <form>
      <div class="row">
        <div class="col-md-2">
          <input  @change="evento => estado.numero1 = parseInt(evento.target.value)" required type="text" placeholder="Numero" class="form-control">
        </div>
        <div class="col-md-2">
          <input  @change="evento => estado.numero2 = parseInt(evento.target.value)" required type="text" placeholder="Numero" class="form-control">
          
        </div>
        <div class="col-md-2">
          <select @change="evento => estado.operacao = evento.target.value" class="form-control">
            <option value="soma">Soma</option>
            <option value="subtrair">Subtrair</option>
            <option value="multiplicar">Multiplicar</option>
            <option value="dividir">Dividir</option>
          </select>
        </div>
      </div>
    </form>
    
    
    <h2>{{ getOperacao() }}</h2>
    
  </div>
  </template>

<style scoped>
  
</style>
