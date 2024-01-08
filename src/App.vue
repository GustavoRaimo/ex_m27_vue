<script setup>
import { reactive, computed } from 'vue';

const estado = reactive({
  num1: 0,
  num2: 0,
  operacao: "+",
});

const resultado = computed(() => {
  const { num1, num2, operacao } = estado;
  switch (operacao) {
    case "+":
      return num1 + num2;
    case "-":
      return num1 - num2;
    case "*":
      return num1 * num2;
    case "/":
      return num1 / num2;
    default:
      return 0;
  }
});
</script>

<template>
  <div class="vh-100 d-flex align-items-center justify-content-center">
    <div class="container">
      <h1 class="text-center mb-5">Calculadora Aritmética</h1>
      <table class="table">
        <thead>
          <tr>
            <th scope="col" class="text-center align-middle">Número 1</th>
            <th scope="col" class="text-center align-middle">Operação</th>
            <th scope="col" class="text-center align-middle">Número 2</th>
            <th scope="col" class="text-center align-middle"></th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>
              <input type="number" v-model="estado.num1" class="form-control text-center">
            </td>
            <td>
              <select v-model="estado.operacao" class="form-control text-center fw-bold">
                <option value="+">Soma</option>
                <option value="-">Subtração</option>
                <option value="*">Multiplicação</option>
                <option value="/">Divisão</option>
              </select>
            </td>
            <td>
              <input type="number" v-model="estado.num2" class="form-control text-center">
            </td>
            <td colspan="2" class="text-center align-middle">
              <p class="fw-bold fs-3">Resultado: {{ resultado }}</p>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<style scoped>
.form-control {
  cursor: pointer;
}
</style>
