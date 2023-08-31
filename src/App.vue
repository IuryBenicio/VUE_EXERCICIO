<script setup>
import { reactive } from 'vue';
////////////////////////////////
import Header from './components/Header.vue';
import Display_form from './components/Display_form.vue';
import Buttons from './components/Buttons.vue';
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
    <Header></Header>
    <form>
      <Display_form :estado_filtro="estado.filtro" :estado_num-a="estado.numA" :estado_num-b="estado.numB" :total="estado.total" 
      :num-a_evento="evento => estado.numA = evento.target.value" :select_evento="evento => estado.filtro = evento.target.value" :num-b_evento="evento => estado.numB = evento.target.value"/>
      <Buttons :getoperacao="getOperacao" :reseta="reseta"/>
    </form>
  </div>
</template>
  
<style scoped>
    form{
        text-align: center;
    }
  .container{
    display: flex;
    flex-direction: column;
    justify-content: center;
    height: 100vh;
  }
</style>
