<script lang="ts">
import { defineComponent } from "vue";
import BarraLateral from "./components/BarraLateral.vue";
import Form from "./components/Form.vue";
import Tarefa from "./components/Tarefa.vue";
import ITarefa from "./interfaces/ITarefa";
import Box from "./components/Box.vue";

export default defineComponent({
  name: "App",
  components: {
    BarraLateral,
    Form,
    Tarefa,
    Box,
  },
  data() {
    return {
      tarefas: [] as ITarefa[],
    };
  },
  computed: {
    listaEstaVazia(): boolean {
      return this.tarefas.length === 0;
    },
  },
  methods: {
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa);
    },
  },
});
</script>

<template>
  <main class="columns is-gapless is-multiline modo-escuro">
    <div class="column is-one-quarter">
      <BarraLateral />
    </div>
    <div class="column is-three-quarter conteudo">
      <Form @aoSalvarTarefa="salvarTarefa" />
      <div class="lista">
        <Tarefa
          v-for="(tarefa, index) in tarefas"
          :key="index"
          :tarefa="tarefa"
        />
        <Box v-if="listaEstaVazia">
          VOCÊ NÃO INICIOU NENHUMA ATIVIDADE HOJE! :(
        </Box>
      </div>
    </div>
  </main>
</template>


<style>
.lista {
  padding: 0.5rem;
}
main {
  --bg-primario: #fff;
  --text-primary: #000;
}
main.modo-escuro {
  --bg-primario: #010f2b;
  --text-primary: #ddd;
}
.conteudo {
  background-color: var(--bg-primario);
  color: var(--text-primary);
}
</style>
