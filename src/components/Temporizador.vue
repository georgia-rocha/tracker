<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <Cronometro :tempoEmSegundos="tempoEmSegundos" />
    <button class="button" @click="iniciar" :disabled="cronometroAtivo">
      <span>play</span>
    </button>
    <button class="button" @click="finalizar" :disabled="!cronometroAtivo">
      <span>stop</span>
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Cronometro from "./Cronometro.vue";

export default defineComponent({
  name: "Temporizador",
  emits: ["tempFinished"],
  components: {
    Cronometro,
  },
  data() {
    return {
      tempoEmSegundos: 0,
      intervalId: null,
      cronometroAtivo: false,
    };
  },

  methods: {
    iniciar() {
      this.finalizar();
      this.cronometroAtivo = true;
      this.intervalId = setInterval(() => {
        this.tempoEmSegundos += 1;
      }, 1000);
      console.log("Iniciando");
    },

    finalizar() {
      if (this.intervalId !== null) {
        this.cronometroAtivo = false;
        clearInterval(this.intervalId);
        console.log("Finalizando");
        this.$emit("tempFinished", this.tempoEmSegundos);
        this.tempoEmSegundos = 0;
        this.intervalId = null;
      }
    },
  },

  beforeDestroy() {
    this.finalizar();
  },
});
</script>

<style scoped>
</style>
