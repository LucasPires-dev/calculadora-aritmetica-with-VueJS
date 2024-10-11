<script setup>
    const props = defineProps(['alteraOTipoDaOperacao','realizarConta', 'resultado'])
</script>

<template>
    <form @submit.prevent="" class="pt-5">
    <div class="row">
      <div class="col-4 text-center" style="border: 2px solid black">
      <span class="text-center m-0 p-0">{{ props.resultado }}</span>
      </div>
      <div class="col-4">
        <select @change="props.alteraOTipoDaOperacao" class="form-control text-center">
          <option value="adicao">+ Somar</option>
          <option value="subtracao">- Subtrair</option>
          <option value="multiplicacao">* Multiplicar</option>
          <option value="divisao">/ Dividir</option>
        </select>
      </div>
      <div class="col-4">
        <input @change="props.realizarConta" type="number" class="form-control text-center">
      </div>
    </div>
  </form>
</template>