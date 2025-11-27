<template>
  <div>
    <h2>Hola mundo desde la vista</h2>
    <Contador tit="Contador 1 enviado desde el padre" :inicio="4+4" :mostrar="true" />
    <Contador tit="Contador 2" inicio="4" :mostrar="false"/>
  </div>
</template>

<script>
import Contador from "../components/Contador.vue";

export default {
    components: {
        Contador
    },

};
</script>

<style>

</style>