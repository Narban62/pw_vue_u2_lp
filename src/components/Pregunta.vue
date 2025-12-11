<template>
  <div class="container">
    <img
      src="https://yesno.wtf/assets/yes/5-64c2804cc48057b94fd0b3eaf323d92c.gif"
      alt="No se pudo visualiar"
    />
    <div class="pregunta_container">
      <input placeholder="HAZME UNA PREGUNTA" type="text" />
      <p>Recuerda terminar con el signo de interrogación "?"</p>
      <h2>¿Sere millonario?</h2>
      <h1>Yes, No</h1>
    </div>
  </div>
</template>

<script>
export default {};
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
</style>