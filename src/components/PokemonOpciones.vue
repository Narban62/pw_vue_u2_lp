<template>
  <div class="opciones_container">
    <ul>
      <li v-on:click="pasarPadre(pokemon.id)" v-for="pokemon in listaPokemons" :key="pokemon.id">{{ pokemon.nombre }}</li>
    
    </ul>
  </div>
</template>

<script>
export default {
  props:{
    listaPokemons:{
      type:Array,
      required:true
    }
  },
  methods:{
    pasarPadre(id){
      this.$emit('seleccionado',id)
    },
  }

};
    
</script>

<style>
.opciones_container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
ul {
  list-style-type: none;
}
li {
    background: white;
    border-radius: 5px;
    border: 1px solid;
    cursor: pointer;
    width: 150px;
    margin-top: 10px;
    text-align: center;
}
</style>