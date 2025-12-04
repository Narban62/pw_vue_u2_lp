<template>
  <div class="view_container">
    <h2>Prueba</h2>
    <Directivas />
  </div>
</template>

<script>
import Directivas from "@/components/Directivas.vue";
export default {
  components: {
    Directivas,
  },
};
</script>

<style scoped>
.view_container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

h2 {
    font-size: 50px;
}

</style>