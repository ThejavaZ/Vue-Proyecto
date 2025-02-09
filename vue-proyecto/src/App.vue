<template>
  <h1>Hello World!</h1>
  <p>Hola {{ nombre }}</p>
  <p>Tu edad es {{ edad + 1 }}</p>

  <h2 v-bind:style="miColor">
    <strong>V-bind</strong> es para aplicarlo a los elementos que se encuentren
    dentro del componente, y es para agregar clases, atributos, estilos, etc.
  </h2>
  <h2 :class="selector">
    <strong>:class</strong> es para aplicarlo a los elementos que se encuentren
    dentro del componente, y es para agregar clases, atributos, estilos, etc.
  </h2>
  <button v-on:click="saludar">Saludar</button>
  <button @click="saludarNombre(nombre)">Saludar {{ nombre }}</button>

  <!-- seccion de contador -->
  <br /><br />
  <span>Contador: {{ contador }}</span>
  <br />
  <button @click="contador++">Incrementar</button>
  <button @click="contador--">Decrementar</button>

  <!-- seccion de contador 2 -->

  <br /><br />
  <span :class="mayorDiez">Contador: {{ contador }}</span>
  <br />
  <button @click="incrementar">Incrementar</button>
  <button @click="decrementar">Decrementar</button>
  <div v-if="contador < 0">Escribe una cantidad mayor a 0</div>
  <div v-else-if="contador > 10">Escribe una cantidad menor a 10</div>
  <div v-else>Cantidad correcta</div>
  <div v-show="comprobar">El numero 0 no esta permitido</div>
</template>

<script setup>
import { ref } from "vue";
// setup es para aplicarlo a todo el componente
//y setup me ahorra la exportacion
const visible = ref(true);
const nombre = "Javier";
const edad = 22;
const miColor = "color: red; font-size: 20px;";
const selector = "azul";
const mayorDiez = ref("mayorDiez");

const contador = ref(0);

const incrementar = () => {
  contador.value++;
  if (contador.value > 10) {
    mayorDiez.value = "mayorDiez";
  } else {
    mayorDiez.value = "azul";
  }
  visible.value = contador.value === 0;
};

const decrementar = () => {
  contador.value--;
  if (contador.value < 0) {
    mayorDiez.value = "mayorDiez";
  } else {
    mayorDiez.value = "azul";
  }
  visible.value = contador.value === 0;
};

const saludar = () => {
  alert("Hola");
};

const saludarNombre = (nombre) => {
  alert(`Hola ${nombre}`);
};

const comprobar = computed(() => {
  return contador.value > 10;
});
</script>

<style scoped>
/*Scoped es para aplicarlo solo a los elementos que se encuentren dentro del componente*/
h1 {
  color: red;
}

.mayorDiez {
  color: green;
}

.azul {
  color: blue;
}

span {
  color: green;
}
</style>
