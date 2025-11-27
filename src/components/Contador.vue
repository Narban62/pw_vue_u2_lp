<template>
  <div>
    <h1>{{tit}}</h1>
    <h2>12</h2>
    <h3>{{ numero + 40  }} </h3>
    <p>
      {{ numero }}
      <sup>2</sup> = {{ calculaCuadrado }}
    </p>
    <p>
      {{ numero }}
      <sup>2</sup> = {{ calculaCuadrado }}
    </p>
    <p>
      {{ numero }}
      <sup>2</sup> = {{ calculaCuadrado }}
    </p>
    <p>
      {{ numero }}
      <sup>2</sup> = {{ calculaCubo }}
    </p>
    <p>
      {{ numero }}
      <sup>2</sup> = {{ obtenerCubo() }}
    </p>
  </div>

  <button @:click="incrementar()">+1</button>
  <button v-on:click="decrementar()">-1</button>
  <button v-show="mostrar">Prueba</button>
</template>

<script>
export default {
  data(){
    return{
      numero:this.inicio,
      titulo:'Contador'
    }
  },
  methods:{
    obtenerCuadrado(){
      console.log('Entro a obtener cuadrado');
      return this.numero*this.numero;
    },
    obtenerCubo(){
      return this.numero*this.numero*this.numero;
    },
    incrementar(){
      console.log(this.tit);
      
      this.numero ++;
    },
    decrementar(){
      this.numero --;
    }

  },
  computed:{
    calculaCuadrado(){
      console.log('Entro a propiedad computada cuadrado');
      
      return this.numero*this.numero;
    },
    calculaCubo(){
      console.log('Entro a propiedad computada cubo');
      
      return this.numero*this.numero*this.numero;
    }
  },

  // props:["tit", "inicio", "mostrar"] declaracion basica de props
  props:{
    tit: String,
    inicio: {
      type:Number,
      default:99,
      validator(value){
        return value > 10;
      }
    },
    mostrar: Boolean,
    
  }

  // String number Bollean Array Object Date Function BigInt

}
</script>

<style>

</style>