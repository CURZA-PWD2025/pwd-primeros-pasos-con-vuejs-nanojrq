<script setup lang="ts">
import FormularioComponent from './components/FormularioComponent.vue'
import ChildComponent from './components/ChildComponent.vue';
import { ref } from 'vue';
const saludar = ref('Hola desde la constante saludo');

</script>

<template>
  <FormularioComponent msj= "Formulario de Registro Inicial"/>

  <ChildComponent/>
  <input type="text" v-model="saludar">

</template>




<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
