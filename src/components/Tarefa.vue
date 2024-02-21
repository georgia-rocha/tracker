<template>
  <div class="box">
    <div class="tarefa">
      <h1 class="">Descrição da Tarefa</h1>
      <Cronometro :tempoEmSegundos="15" />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Cronometro from "./Cronometro.vue";

export default defineComponent({
  name: "Tarefa",
  components: {
    Cronometro,
  },
});
</script>

<style scoped>
.box {
  background: #faf0ca;
}
.tarefa {
  display: flex;
  justify-content: space-around;
}
</style>