<script setup>
import {reactive, ref, onMounted} from 'vue';
import Formulario from './components/Formulario.vue';

const estado = reactive({
  NumeroASerConvertido: 0,
  filtro: 'pesoChileno',
});

const resultado = ref('Calculando');

const pesoChilenoReal = async ({NumeroASerConvertido} = estado) => {
  const response = await fetch("https://api.currencybeacon.com/v1/latest?api_key=kBzvus0ucU6oKf0dlzKxP1gGHJKzckRF&base=CLP");
  const data = await response.json();
  const exchangeRate = data.rates.BRL;
  return NumeroASerConvertido * exchangeRate;
};

const dolarReal = async ({NumeroASerConvertido} = estado) => {
  const response = await fetch("https://api.currencybeacon.com/v1/latest?api_key=kBzvus0ucU6oKf0dlzKxP1gGHJKzckRF&base=USD");
  const data = await response.json();
  const exchangeRate = data.rates.BRL;
  return NumeroASerConvertido * exchangeRate;
};

const euroReal = async ({NumeroASerConvertido} = estado) => {
  const response = await fetch("https://api.currencybeacon.com/v1/latest?api_key=kBzvus0ucU6oKf0dlzKxP1gGHJKzckRF&base=EUR");
  const data = await response.json();
  const exchangeRate = data.rates.BRL;
  return NumeroASerConvertido * exchangeRate;
};

const wonReal = async ({NumeroASerConvertido} = estado) => {
  const response = await fetch("https://api.currencybeacon.com/v1/latest?api_key=kBzvus0ucU6oKf0dlzKxP1gGHJKzckRF&base=KRW");
  const data = await response.json();
  const exchangeRate = data.rates.BRL;
  return NumeroASerConvertido * exchangeRate;
};

const ieneReal = async ({NumeroASerConvertido} = estado) => {
  const response = await fetch("https://api.currencybeacon.com/v1/latest?api_key=kBzvus0ucU6oKf0dlzKxP1gGHJKzckRF&base=JPY");
  const data = await response.json();
  const exchangeRate = data.rates.BRL;
  return NumeroASerConvertido * exchangeRate;
};

const realPesoChileno = async ({NumeroASerConvertido} = estado) => {
  const response = await fetch("https://api.currencybeacon.com/v1/latest?api_key=kBzvus0ucU6oKf0dlzKxP1gGHJKzckRF&base=CLP");
  const data = await response.json();
  const exchangeRate = data.rates.BRL;
  return NumeroASerConvertido / exchangeRate;
};

const realDolar = async ({NumeroASerConvertido} = estado) => {
  const response = await fetch("https://api.currencybeacon.com/v1/latest?api_key=kBzvus0ucU6oKf0dlzKxP1gGHJKzckRF&base=USD");
  const data = await response.json();
  const exchangeRate = data.rates.BRL;
  return NumeroASerConvertido / exchangeRate;
};

const realEuro = async ({NumeroASerConvertido} = estado) => {
  const response = await fetch("https://api.currencybeacon.com/v1/latest?api_key=kBzvus0ucU6oKf0dlzKxP1gGHJKzckRF&base=EUR");
  const data = await response.json();
  const exchangeRate = data.rates.BRL;
  return NumeroASerConvertido / exchangeRate;
};

const realWon = async ({NumeroASerConvertido} = estado) => {
  const response = await fetch("https://api.currencybeacon.com/v1/latest?api_key=kBzvus0ucU6oKf0dlzKxP1gGHJKzckRF&base=KRW");
  const data = await response.json();
  const exchangeRate = data.rates.BRL;
  return NumeroASerConvertido / exchangeRate;
};

const realIene = async ({NumeroASerConvertido} = estado) => {
  const response = await fetch("https://api.currencybeacon.com/v1/latest?api_key=kBzvus0ucU6oKf0dlzKxP1gGHJKzckRF&base=JPY");
  const data = await response.json();
  const exchangeRate = data.rates.BRL;
  return NumeroASerConvertido / exchangeRate;
};

const calculateResult = async () => {
  const {filtro} = estado;

  switch (filtro) {
    case 'dolarReal':
      resultado.value = await dolarReal();
      break;
    case 'euroReal':
      resultado.value = await euroReal();
      break;
    case 'wonReal':
      resultado.value = await wonReal();
      break;
    case 'ieneReal':
      resultado.value = await ieneReal();
      break;
    case 'realPesoChileno':
      resultado.value =  await realPesoChileno();
      break;
    case 'realDolar':
      resultado.value = await realDolar();
      break;
    case 'realEuro':
      resultado.value = await realEuro();
      break;
    case 'realWon':
      resultado.value = await realWon();
      break;
    case 'realIene':
      resultado.value = await realIene();
      break;
    default:
      resultado.value = await pesoChilenoReal();
  }
};

onMounted(calculateResult);
</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 text-center">
      <h1>Conversão de moedas:</h1>
    </header>
    <Formulario
        :trocar-filtro="(event) => { estado.filtro = event.target.value; calculateResult(); }"
        :numero1="(event) => { estado.NumeroASerConvertido = Number(event.target.value); calculateResult(); }"
    />
    <br>
    <br>
    <h1 class="text-center border border-dark rounded p-5">O resultado é: {{ resultado }} </h1>
  </div>
</template>

<style scoped>
</style>