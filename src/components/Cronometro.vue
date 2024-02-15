<template>
  <section>
    <strong>{{ tempoDecorrido }}</strong>
  </section>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Cronometro",
  props: {
    tempoEmSegundos: {
      type: Number,
      default: 0,
    },
  },
  computed: {
    tempoDecorrido(): string {
      return this.formatarTempo(this.tempoEmSegundos);
    },
  },
   methods: {
    formatarTempo(segundos: number): string {
      const horas = Math.floor(segundos / 3600);
      const minutos = Math.floor((segundos % 3600) / 60);
      const segundosRestantes = segundos % 60;

      const formatarNumero = (num: number): string => (num < 10 ? `0${num}` : `${num}`);

      return `${formatarNumero(horas)}:${formatarNumero(minutos)}:${formatarNumero(segundosRestantes)}`;
    },
    },
});
</script>

<style scoped>
</style>
