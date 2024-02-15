<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <Cronometro :tempoEmSegundos="tempoEmSegundos" />
    <button class="button" @click="iniciar" :disabled="cronometroAtivo">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button class="button" @click="finalizar" :disabled="!cronometroAtivo">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Cronometro from "./Cronometro.vue";

export default defineComponent({
  name: "Temporizador",
  components: {
    Cronometro
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
        this.intervalId = null;
        console.log("Finalizando");
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
