<script setup>
import { reactive, ref } from "vue";

const language = ref();

const estado = reactive({
  numero1: 0,
  numero2: 0,
});

function Calculadora(language) {
  if (language == "+") {
    return parseInt(estado.numero1) + parseInt(estado.numero2);
  } else if (language == "-") {
    return estado.numero1 - estado.numero2;
  } else if (language == "/") {
    return (estado.numero1 / estado.numero2).toFixed(2);
  } else if (language == "*") {
    return estado.numero1 * estado.numero2;
  }
}
</script>

<template>
  <div class="container">
    <div class="calculadora">
      <h1>Calculadora</h1>

      <form>
        <label for="Numero1">Pimeiro Numero:</label><br />
        <input
          @keyup="(evento) => (estado.numero1 = evento.target.value)"
          type="nunber"
          id="Numero1"
        /><br />
        <label for="Numero">Segundo Numero:</label><br />
        <input
          @keyup="(evento) => (estado.numero2 = evento.target.value)"
          type="nunber"
          id="Numero2"
        /><br /><br />

        <br />
        <label>Selecione a operação:</label>
        <br>
        <select v-model="language" name="operacao" id="">
          <option value="+">Adição</option>
          <option value="/">Divisão</option>
          <option value="-">Subtração</option>
          <option value="*">Multiplicação</option>
        </select>

        <br />

        <span>Resultado: {{ Calculadora(language) }}</span
        ><br />
      </form>
    </div>
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  text-align: center;
}

.container {
  display: flex;
  align-items: center;
  justify-content: center;

  height: 97vh;
}

select{
  text-align: center;
  width: 100%;
}
</style>
