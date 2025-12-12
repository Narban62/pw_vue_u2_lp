<template>
  <div class="container">
    <img
    v-if="imagen"
      :src="imagen"
      alt="No se pudo visualiar"
    />
    <div class="pregunta_container">
      <input v-model="pregunta"  placeholder="HAZME UNA PREGUNTA" type="text" />
      <p>Recuerda terminar con el signo de interrogación "?"</p>
      <h2>{{ pregunta }}</h2>
      <h1 >{{respuesta}}</h1>
    </div>
  </div>
</template>

<script>
import { consumirAPIFacade } from '@/clients/YesNoClient.js';
export default {
  data(){
    return{
      pregunta:null, 
      respuesta:null,
      imagen:null,
    }
  },
  watch:{
    //son observadores de propiuedades reactivas
     pregunta(value, oldValue){
      // console.log(value);
      // console.log(oldValue);
      if (value.includes('?')) {
        //llamar al API
        this.respuesta = 'pensando ..... wa'
        this.consumir();
        // const resp = consumirAPIFacade();
        // console.log(resp);
        // console.log(resp.answer);
        
        
        
        
      }
     },
  },
  methods:{
    async consumir(){
       const resp =  await consumirAPIFacade();
       this.imagen = resp.image;
       this.respuesta = resp.answer;
       
    }
  }
};
</script>



<style>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 10px;
  
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

img {
  height: 100vh;
  width: 100vw;
  max-height: 100%;
  max-width: 100%;
  position: fixed;
  left: 0px;
  top: 0px;
}

.pregunta_container {
  position: relative;
  min-height: 100vh; /* altura de toda la pantalla */
  display: flex;
  flex-direction: column; 
  justify-content: center; /* centrado vertical */
  align-items: center; /* centrado horizontal */
}

input {
    width: 250px;
    padding: 10px 15px;
    border-radius: 5px;
    border: none;
}
input:focus{
    outline: none;

}
h1,h2,p {
color: white;
}

p {
    font-size: 20px;
}

h2 {
    margin-top: 150px;
}
body {
  background: black;
  
}
</style>