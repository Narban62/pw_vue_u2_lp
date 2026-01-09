<template>
    <div class="container">
    <h1 v-if="gana">Has Seleccionado el Pokemon Correcto</h1>
    <h1 v-if="pierde">Has Seleccionado el Pokemon Incorrecto</h1>
    </div>
  <PokemonImagen :pokemonId="pokemonGanador" />
  <PokemonOpciones :listaPokemons="poekemonArr" @seleccionado="evaluarGanador($event)" />
</template>

<script>
import PokemonImagen from "@/components/PokemonImagen.vue";
import PokemonOpciones from "@/components/PokemonOpciones.vue";
import { obtenerPokemonFachada,obtenerAleatorioFachada } from "@/clients/PokemonClient";
export default {
  components: {
    PokemonImagen,
    PokemonOpciones,
  },
  mounted(){
    this.iniciarJuego();
  },
  data(){
    return{
        poekemonArr:[],
        pokemonGanador:null,
        gana:false,
        pierde:false
    }
  },
  methods:{
    async iniciarJuego(){
        this.poekemonArr =  await obtenerPokemonFachada();
        const objAleatorio = obtenerAleatorioFachada(0,3);
        this.pokemonGanador = this.poekemonArr[objAleatorio].id;
    },
    evaluarGanador(idGanador){
        console.log('Valor Recibido desde padre');
        console.log(idGanador);
        if (idGanador === this.pokemonGanador) {
            console.log('ganador');
            this.gana = true;
            this.pierde =  false;
            this.limpiarMensajes()
            
        }else{
            console.log('perdedor');
            this.pierde =  true;
            this.gana =  false;
            this.limpiarMensajes()
        }
        this.limpiarMensajes();
        
    },
    limpiarMensajes(){
        setTimeout(() => {
            this.gana = false;
            this.pierde = false;
        }, 5000);
    }
    

  }
};
</script>

<style>
.container{
    display: flex;
    align-content: center;
    justify-content: center;
}
</style>