<script setup>
  import { reactive } from 'vue';

  const estado = reactive({
    number1: 0,
    number2: 0,
    operacoesAritemeticas: '',
    resultado: 0,
  })

  const somar = (a, b) => a + b;
  const subtrair = (c, d) => c - d;
  const divisao = (e, f) => e / f;
  const multiplica = (g, h) => g * h;

  const selecionaOperacao = () => {
    const {operacoesAritemeticas, number1, number2} = estado;

    switch (operacoesAritemeticas) {
      case 'adicao':
        return estado.resultado = somar(number1, number2);
      case 'subtracao':
        return estado.resultado = subtrair(number1, number2);
      case 'divisao':
        return estado.resultado = divisao(number1, number2);
      case 'multiplicacao':
        return estado.resultado = multiplica(number1, number2);
    }
  }

  selecionaOperacao();
</script>

<template>
  <div class="container mt-5 ms-5">
    <div class="row">
        <div class="col-md-4">
          <input v-model="estado.number1" type="number" placeholder="digite o numero">
          <input v-model="estado.number2" type="number" placeholder="digite o numero">
        </div>
      <div class="col-md-4">
        <select v-model="estado.operacoesAritemeticas"  @change="selecionaOperacao">
            <option value="adicao">Adição</option>
            <option value="subtracao">Subtração</option>
            <option value="divisao">Divisão</option>
            <option value="multiplicacao">Multiplicação</option>
          </select>
      </div>
      <div class="col-md-2">
        <span>Resultado é {{ estado.resultado }} </span>
      </div>
    </div>
  </div>
</template>
