<script setup>
  import { reactive, ref } from 'vue';

  const estado = reactive ({
    operacao: 'soma',
    numOne: 0,
    numTwo: 0,
  })

  const resultado = ref(0);

  const getSoma = () => {
    return estado.numOne + estado.numTwo;
  }  
  
  const getSubtrai = () => {
    return estado.numOne - estado.numTwo;
  }  
  
  const getDivide = () => {
    return estado.numOne / estado.numTwo;
  }  
  
  const getMultiplica = () => {
    return estado.numOne * estado.numTwo;
  }  
  
  const calcular = () => {
    switch (estado.operacao) {
      case 'soma':
        resultado.value = getSoma();
        break;
      case 'subtrai':
        resultado.value = getSubtrai();
        break;
      case 'multiplica':
        resultado.value = getMultiplica();
        break;
      case 'divide':
        resultado.value = getDivide();
        break;
    }
  }

  const trocarOperacao = (event) => {
    estado.operacao = event.target.value;
    calcular();
  }

</script>

<template>
  <div class="container">
    <header class="header">
      <h1>Calculadora</h1>
    </header>
    <form class="form-control">
      <ul class="form-group">
        <li class="form-group-item">
          <input v-model.number="estado.numOne" type="number">
          <input v-model.number="estado.numTwo" type="number"><br>
        </li>
        <select @change="trocarOperacao"  class="mt-3 me-3">
          <option value="soma">Somar</option>
          <option value="subtrai">Subtrair</option>
          <option value="divide">Dividir</option>
          <option value="multiplica">Multiplicar</option>
        </select>
        <span>{{ resultado }}</span>
      </ul>
    </form>
  </div>
</template>

<style scoped>

  * {
    list-style: none;
  }
  .header {
    background-color: #ccc;
    text-align: center;
    border-radius: 12px;
  }
</style>
