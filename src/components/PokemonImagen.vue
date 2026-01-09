<template>
  <div class="pokemon_container">
    <img
      :src=srcImagen
      alt="No se puede renderizar"
    />
  </div>
</template>

<script>
export default {
  beforeUnmount(){
    console.log('beforeUnmount: justo antes de que el componente se destruya');
    
  },
  unmounted(){
    console.log('unmounted: se ejecuta cuando fue removido del DOM');
    
  },
    props:{
        pokemonId: {
            type:Number,
            required:true,
        }
    },
    computed:{
        srcImagen(){
            return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.pokemonId}.svg`
            
        }
    }
};
</script>

<style>
.pokemon_container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

img {
    /* position: relative; */
  height: 200px;
  /* right: 10%; */
}
</style>