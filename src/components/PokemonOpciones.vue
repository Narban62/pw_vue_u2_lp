<template>
  <div class="opciones_container">
    <ul>
      <li>Pokemon 1</li>
      <li>Pokemon 2</li>
      <li>Pokemon 3</li>
      <li>Pokemon 4</li>
    </ul>
  </div>
</template>

<script>
export default {};
    
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