<template>
  <div class="box">
    <div class="columns">
      <div
        class="column is-8 is-full"
        is-full
        aqui
        role="form"
        aria-label="Formulário para criação de uma nova tarefa"
      >
        <input
          type="text"
          class="input"
          placeholder="Qual tarefa você deseja iniciar?"
          v-model="description"
        />
        <div class="column">
         <Temporizador @tempFinished="finalizarTarefa" />
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Temporizador from "./Temporizador.vue";

export default defineComponent({
  name: "Form",
  components: {
    Temporizador
  },
  data () {
    return {
      description: ''
    }
  },
  methods: {
    finalizarTarefa (tempoDecorrido: number): void {
      console.log('tempo da tarefa', tempoDecorrido);
      console.log('descrição da tarefa', this.description);
    }
  }
  
});
</script>

<style scoped>
</style>