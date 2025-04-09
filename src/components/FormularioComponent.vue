<script setup lang="ts">

import { ref } from 'vue';

defineProps<{
    msj?: String
}>()


const nombre = ref('');
const email = ref('');
const password = ref('');
const fechaNacimiento = ref('');
const edad = ref(''); 


const enviar= ()=> {
    if (nombre.value && email.value && password.value && fechaNacimiento.value) {
        alert(`Nombre: ${nombre.value}, Email: ${email.value}, Contraseña: ${password.value}, Fecha de Nacimiento: ${fechaNacimiento.value}`);

        let persona = {
            nombre: nombre.value,
            email: email.value,
            password: password.value,
            fechaNacimiento: fechaNacimiento.value,
            edad: edad.value
        };
        console.log(persona); //imprimir el objeto en la consola


        //limpiar los campos
        nombre.value = '';  
        email.value = '';
        password.value = '';
        calcularEdad(); //calcular la edad
        fechaNacimiento.value = '';
    }  
    else {
        alert('Por favor, completa todos los campos.');
    }
};

const calcularEdad = () => {
    console.log(fechaNacimiento);
    const naciomiento = new Date(fechaNacimiento.value);
    const hoy = new Date();
    let calcular = hoy.getFullYear() - naciomiento.getFullYear();
    const mes = hoy.getMonth() - naciomiento.getMonth();
    if (mes < 0 || (mes === 0 && hoy.getDate() < naciomiento.getDate())) {
        calcular--;
    }
    alert(`Tu edad es: ${calcular}`);
    edad.value = calcular.toString()
    return edad;
};

</script>





<template>

<h2> {{ msj }}</h2>

<div class="contenedorform">

  <form action=" ">
    <input type="text" placeholder="Nombre" v-model="nombre" /> <br>
    <input type="email" placeholder="Email" v-model="email" /> <br>
    <input type="password" placeholder="Contraseña" v-model="password" /> <br>
    <input type="date" placeholder="Fecha de Nacimiento" v-model="fechaNacimiento" /> <br>
    <button class="boton" @click="enviar()"> Enviar</button>
  </form>

    <h4>Datos ingresados:</h4>
    <div>
      <p>Nombre: {{ nombre }}</p> 
      <p>Email: {{ email }}</p>
      <p>Contraseña: {{ password }}</p>
      <p>Fecha de Nacimiento: {{ fechaNacimiento }}</p>
      <p>Edad: {{ edad }}</p>
    </div>
</div>



</template>




<style scoped>

.contenedorform {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

#input {
  margin: 10px 0;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  width: 300px;
} 

.boton {
  background-color: #42b883;
  color: white;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
  border-radius: 5px;
  margin-top: 15px;
  font-size: 16px;
}


</style>