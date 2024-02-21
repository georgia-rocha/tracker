<template>
  <div class="box">
    <div class="tarefa">
      <h1 class="">Descrição da Tarefa</h1>
      <Cronometro :tempoEmSegundos="15" />
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
      type: Object as PropType<ITarefa>
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