<template>
  <div class="container">
    <h1 v-if="gana">Has Seleccionado el Pokemon Correcto</h1>
    <button @click="destruirObjeto()" >Destruir</button>
    <h1 v-if="pierde">Has Seleccionado el Pokemon Incorrecto</h1>
  </div>
  <PokemonImagen v-if="mostrar" :pokemonId="pokemonGanador" />
  <PokemonOpciones
    :listaPokemons="poekemonArr"
    @seleccionado="evaluarGanador($event)"
  />
</template>

<script>
import PokemonImagen from "@/components/PokemonImagen.vue";
import PokemonOpciones from "@/components/PokemonOpciones.vue";
import {
  obtenerPokemonFachada,
  obtenerAleatorioFachada,
} from "@/clients/PokemonClient";
export default {
  components: {
    PokemonImagen,
    PokemonOpciones,
  },
  //   Crea el Componente
  beforeCreate() {
    console.log("beforeCreated: Apenas inicia la instancia del componente");
  },
  created() {
    console.log("Created: Cuando ya han pasado data, computed, methods, watch");
  },
  //   Montaje del componente, cuando se renderiza o se visualiza el componente
  beforeMount() {
    console.log('beforeMount: justo antes de renderizar el primer elemento html');
  },
  mounted() {
    console.log('Cuando el componente ya se renderizo');
    
    this.iniciarJuego();
  },

//   Actualizacion de un componente 
  beforeUpdate(){
    console.log('beforeUpdate: cuando cambio un data o un props y vue esta por renderizar el cambio');
    
  },
  updated(){
    console.log('updated: cuando ya se actualizo, despues de la re-renderizacion');
    this.limpiarMensajes();
  },
//   Cuando desmontamos el componente

  beforeUnmount(){
    console.log('beforeUnmount: justo antes de que el componente se destruya');
    
  },
  unmounted(){
    console.log('unmounted: se ejecuta cuando fue removido del DOM');
    
  },
  
  data() {
    return {
      poekemonArr: [],
      pokemonGanador: null,
      gana: false,
      pierde: false,
      mostrar:true,
    };
  },
  methods: {
    async iniciarJuego() {
      this.poekemonArr = await obtenerPokemonFachada();
      const objAleatorio = obtenerAleatorioFachada(0, 3);
      this.pokemonGanador = this.poekemonArr[objAleatorio].id;
    },
    evaluarGanador(idGanador) {
      console.log("Valor Recibido desde padre");
      console.log(idGanador);
      if (idGanador === this.pokemonGanador) {
        console.log("ganador");
        this.gana = true;
        this.pierde = false;
      } else {
        console.log("perdedor");
        this.pierde = true;
        this.gana = false;
      }
      
    },
    limpiarMensajes() {
      setTimeout(() => {
        this.gana = false;
        this.pierde = false;
      }, 5000);
    },
    destruirObjeto(){
        this.mostrar = false;
    }
  },
};
</script>

<style>
.container {
  display: flex;
  align-content: center;
  justify-content: center;
}
</style>