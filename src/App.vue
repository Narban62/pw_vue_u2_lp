<template>
  <div>
    <!-- <ContadorView /> -->
    <!-- <Contador /> -->
     <!-- <DirectivasView/> -->
     <!-- <PreguntaView/> -->
     <PokemonView/>

    
  </div>
</template>

<script>
  import PokemonView from './views/PokemonView.vue';
import ContadorView from '../src/views/ContadorView.vue'
// import Contador from "../src/components/Contador.vue"
import DirectivasView from './views/DirectivasView.vue';
import PreguntaView from './views/PreguntaView.vue';
export default {
components:{
  ContadorView,DirectivasView,PreguntaView, PokemonView
},
};
</script>

<style>

</style>