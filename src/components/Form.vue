<template>
  <div class="box">
    <div class="columns">
      <div
        class="column is-8 is-full" is-full aqui 
        role="form"
        aria-label="Formulário para criação de uma nova tarefa"
      >
        <input
          type="text"
          class="input"
          placeholder="Qual tarefa você deseja iniciar?"
        />
        <div class="column">
          <div
            class="is-flex is-align-items-center is-justify-content-space-between"
          >
           <Cronometro :tempoEmSegundos="tempoEmSegundos"/>

            <button class="button" @click="iniciar">
              <span class="icon">
                <i class="fas fa-play"></i>
              </span>
              <span>play</span>
            </button>
            <button class="button" @click="finalizar">
              <span class="icon">
                <i class="fas fa-stop"></i>
              </span>
              <span>stop</span>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">

import { defineComponent } from "vue";
import Cronometro from './Cronometro.vue';

export default defineComponent({
  name: "Form",
  components: {
    Cronometro
  },
  data() {
    return {
      tempoEmSegundos: 0,
      intervalId: null,
    };
  },
 
  methods: {
    iniciar() {
      this.finalizar();
      this.intervalId = setInterval(() => {
        this.tempoEmSegundos += 1;
      }, 1000);
      console.log("Iniciando");
    },

    finalizar() {
      if (this.intervalId !== null) {
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