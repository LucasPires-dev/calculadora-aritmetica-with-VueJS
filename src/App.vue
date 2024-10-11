<script setup>
  import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue';
import Formulario from './components/Formulario.vue';

  const estado = reactive({
    input: 10,
    tipoDaOperacao: "adicao",
    resultado: 0
  })

  const alteraOTipoDaOperacao = (evento ) => {
    estado.tipoDaOperacao = evento.target.value
  }

  const realizarConta = (evento) => {
    
    const {tipoDaOperacao, input} = estado;

    estado.input = evento.target.value


    const somar =() => {
      estado.resultado = estado.resultado + parseInt(estado.input)
  }

  const subtrair =() => {
    estado.resultado = estado.resultado - parseInt(estado.input)
  }

  const multiplicar =() => {
    estado.resultado = estado.resultado * parseInt(estado.input)
  }

  const dividir =() => {
    if(parseInt(estado.input) === 0){
      alert("Erro: Não é possível divisão por ZERO!")
    }else{
    estado.resultado = estado.resultado / parseInt(estado.input)
  }
  }

    switch (tipoDaOperacao) {
      case 'adicao':
        return somar()
      
      case 'subtracao':
        return subtrair()
      
      case 'multiplicacao':
        return multiplicar()

      case 'divisao':
        return dividir()
    }
  }

</script>

<template>
   <Cabecalho/>
  <div class="container">
      <Formulario :resultado="estado.resultado" :altera-o-tipo-da-operacao="alteraOTipoDaOperacao" :realizar-conta="realizarConta"/>
  </div>
</template>

<style scoped>

</style>
