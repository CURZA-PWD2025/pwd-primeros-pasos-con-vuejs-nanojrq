<script setup lang="ts">

const propiedad = defineProps<{
    mensaje: {Type: String, default: "mensaje por default"},
    saludo:{ Type: string, default: "saludo por default"}
}>()


</script>



<template>
    <div>
        <h1>Hola desde el hijo</h1>
        <p>{{ propiedad.mensaje }}</p>
        <p>{{ propiedad.saludo }}</p>
    </div>




</template>





<style scoped></style>