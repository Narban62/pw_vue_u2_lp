<template>
  <div class="container">
    <label for="id_nombre">Nombre</label>
    <input v-model="nombre" id="id_nombre" type="text" />
    <p>{{ nombre }}</p>

    <label for="id_apellido">Apellido</label>
    <input v-model="apellido" id="id_apellido" type="text" />
    <p>{{ apellido }}</p>

    <!-- <h1>{{ arreglo }}</h1> -->

    <hr />
    <label for="id_nombre_1">Nombre</label>
    <input v-model="nombre1" id="id_nombre_1" type="text" />
    <br>
    <label for="id_apellido_1">Apellido</label>
    <input v-model="apellido1" v-on:keypress.enter="agregarEstudiante1" id="id_apellido_1" type="text" />

    <!--  -->
    <ul>
      <div>
        <li
          v-show="nombre"
          v-for="{ nombre, apellido } in arreglo"
          :key="nombre"
        >
          {{ nombre }} {{ apellido }}
        </li>
      </div>
    </ul>

    <h2>Tabla</h2>

    <table border="1">
      <thead>
        <tr>
          <th>Nombre</th>
          <th>Apellido</th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-show="nombre && apellido"
          v-for="{ nombre, apellido } in arreglo"
          :key="nombre"
        >
          <td>{{ nombre }}</td>
          <td>{{ apellido }}</td>
        </tr>
      </tbody>
    </table>

    <button v-on:click="imprimirNombre()">Imprimir Nombre</button>
    <button v-on:click="agregarEstudiante()">Agregar Estudiante</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nombre: null,
      apellido: null,
      nombre1: null,
      apellido1: null,
      arreglo: [],
    };
  },
  methods: {
    imprimirNombre() {
      console.log(this.nombre);
    },
    agregarEstudiante() {
      const estu = {
        nombre: this.nombre,
        apellido: this.apellido,
      };
      console.log("Se agrega estudiante");
      console.log(estu);
      this.arreglo.push(estu);
      this.limpiarFormulario();
    },
    agregarEstudiante1(event) {
      console.log('event');
      
      if (event.charCode !== 13) {
        return;
      } else {
        console.log("presiono el enter");

        const estu = {
          nombre: this.nombre1,
          apellido: this.apellido1,
        };
        console.log("Se agrega estudiante");
        console.log(estu);
        this.arreglo.push(estu);
        this.limpiarFormulario();
      }
    },
    limpiarFormulario() {
      this.nombre = null;
      this.apellido = null;
      this.nombre1 = null;
      this.apellido1 = null;

    },
  },
};
</script>

<style>




</style>