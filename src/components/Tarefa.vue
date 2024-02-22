<template>
  <div class="box">
    <div class="tarefa">
      <h1 class="">{{tarefa.description || 'Tarefa sem Descrição'}}</h1>
      <Cronometro :tempoEmSegundos="tarefa.duracaoEmSegundos" />
    <div class="apagar-tarefa" @click="excluirTarefa">APAGAR</div>
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
  },
   methods: {
    excluirTarefa() {
      this.$emit("excluirTarefa");
    },
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
.apagar-tarefa{
  color: red
}
</style>