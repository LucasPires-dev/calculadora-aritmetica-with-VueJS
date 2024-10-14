<script setup>
  import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue';
import Formulario from './components/Formulario.vue';

  const estado = reactive({
    campo1: 0,
    campo2: 0,
    tipoDaOperacao: null,
    resultado: ''
  })



  const alteraOTipoDaOperacao = (evento ) => {
    estado.tipoDaOperacao = evento.target.value
    calcular()
  }

  const getNumber1 = (evento) => {
    estado.campo1 = parseInt(evento.target.value)
    calcular()
    // estado.resultado = parseInt(campo1) + estado.campo2
  }

  const getNumber2 = (evento) => {
    estado.campo2 = parseInt(evento.target.value)
    calcular()
    // estado.resultado = parseInt(campo2) + estado.campo1
  }

  const calcular = () => {
    console.log(estado)
    const {tipoDaOperacao, campo1, campo2, resultado} = estado;

    const somar =() => {
      estado.resultado = parseInt(campo2) + parseInt(campo1)
  }

  const subtrair =() => {
    estado.resultado = parseInt(campo2) - parseInt(campo1)
  }

  const multiplicar =() => {
    estado.resultado = parseInt(campo2) * parseInt(campo1)
  }

  const dividir =() => {
    if(parseInt(campo1) === 0){
      alert("Erro: Não é possível divisão por ZERO!")
    }else{
    estado.resultado = parseInt(campo1) / parseInt(campo2)
  }
  }

    switch (tipoDaOperacao) {
      case 'soma':
        return somar()
      
      case 'subtracao':
        return subtrair()
      
      case 'multiplicacao':
        return multiplicar()

      case 'divisao':
        return dividir()

      default:
        return null
    }

  }

  const resultado = () => {
    return estado.resultado
  }

</script>

<template>
   <Cabecalho/>
    <main class="d-flex justify-content-center align-items-center" style="height: calc(100vh - 60px);">
        <div class="container">
            <Formulario :altera-o-tipo-da-operacao="alteraOTipoDaOperacao" :calcular="calcular" :get-number1="getNumber1" :get-number2="getNumber2" :resultado="resultado" />
        </div>
    </main>
</template>

<style scoped>

</style>
