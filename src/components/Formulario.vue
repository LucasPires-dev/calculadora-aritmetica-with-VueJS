<script setup>
const props = defineProps(['alteraOTipoDaOperacao', 'calcular', 'resultado', 'getNumber1', 'getNumber2'])
</script>

<template>
  <div class="card mx-auto" style="max-width: 360px; width: 100%;">
    <div class="card-body">
      <div class="mb-3">
        <input type="number" class="form-control" id="num1" placeholder="Primeiro Número" @change="getNumber1">
      </div>
      <div class="mb-3">
        <input type="number" class="form-control" id="num2" placeholder="Segundo Número" @change="getNumber2">
      </div>
      <div class="mb-3">
        <select class="form-select" id="operacao" @change="alteraOTipoDaOperacao">
          <option value="">Selecione a Operação</option>
          <option value="soma">Soma</option>
          <option value="subtracao">Subtração</option>
          <option value="multiplicacao">Multiplicação</option>
          <option value="divisao">Divisão</option>
        </select>
      </div>
      <button class="btn btn-success w-100" id="calcular" @click="calcular" disabled>Calcular</button>
      <div id="resultado" class="mt-3 text-center" ><strong>Resultado: {{ resultado() }}</strong></div>
    </div>
  </div>
</template>