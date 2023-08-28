<script setup>
import { reactive } from 'vue';
////////////////////////////////
const estado = reactive({
  total: "...",
  numA: '',
  numB: '',
  filtro: 'selecione qual será a operação',
})

const soma = () => {
  const resultadoSoma = parseInt(estado.numA) + parseInt(estado.numB)
  estado.total = resultadoSoma;
  return estado.total
}
const multiplica = () => {
  const resultadoMult = parseInt(estado.numA) * parseInt(estado.numB)
  estado.total = resultadoMult;
  return estado.total
}
const divide = () => {
  const resultadoDivide = parseInt(estado.numA) / parseInt(estado.numB)
  estado.total = resultadoDivide;
  return estado.total
}
const subtrai = () => {
  const resultadoSubtrai = parseInt(estado.numA) - parseInt(estado.numB)
  estado.total = resultadoSubtrai;
  return estado.total
}

const reseta = () =>{
  estado.total = '...'
  estado.numA = ' '
  estado.numB = ' '
  estado.filtro = 'selecione qual será a operação'
}

const getOperacao = () => {
  const {filtro} = estado;
  switch(filtro){
    case '+':
      return soma();
    case '*':
      return multiplica();
    case '/':
      return divide();
    case '-':
      return subtrai();
    default:
      return '...'
  }
}

</script>

<template>
  <div class="container">
    <h1 class="text-center mb-3">CALCULADORA SIMPLES</h1>
    <form>
      <div class="display mb-2 rounded">
        {{ estado.total }}
      </div>
      <div class="input-group">
        <span class="input-group-text">Primeiro número</span>
        <input @keyup="evento => estado.numA = evento.target.value" type="text" class="form-control">
        <span class="input-group-text">operação</span>
        <select @change="evento => estado.filtro = evento.target.value" class="form-control">
          <option value="selecionar">selecionar</option>
          <option value="+">+</option>
          <option value="*">*</option>
          <option value="/">/</option>
          <option value="-">-</option>
        </select>
        <span class="input-group-text">Segundo número</span>
        <input @keyup="evento => estado.numB = evento.target.value" type="text" class="form-control">
      </div>
      {{ estado.numA +'  '+estado.filtro+'  '+ estado.numB + ' = '+ estado.total}}
      <div class="botoes">
        <button @click="getOperacao()" type="button" class="btn btn-success mt-2">=</button>
        <button @click="reseta()" type="reset" class="mt-2 btn btn-secondary">Resetar</button>
      </div>
    </form>
  </div>
</template>
  
<style scoped>
  form{
    text-align: center;
  }
  .botoes{
    display: flex;
    justify-content: space-between;
  }
  .btn{
    width: 49.5%;
  }
  .display{
    text-align: center;
    font-size: 20px;
    width: 100%;
    padding: 4px;
    background-color: rgb(189, 189, 189);
  }
  .container{
    display: flex;
    flex-direction: column;
    justify-content: center;
    height: 100vh;
  }
</style>
