<template>
  <div class="box">
    <div class="tarefa">
      <h1 class="">{{tarefa.description || 'Tarefa sem Descrição'}}</h1>
      <Cronometro :tempoEmSegundos="tarefa.duracaoEmSegundos" />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import Cronometro from "./Cronometro.vue";
import ITarefa from "../interfaces/ITarefa"

export default defineComponent({
  name: "Tarefa",
  components: {
    Cronometro,
  },
  props: {
    tarefa: {
      type: Object as PropType<ITarefa>,
      required: true
    }
  }
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