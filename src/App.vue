<script lang="ts">
import { defineComponent } from "vue";
import BarraLateral from "./components/BarraLateral.vue";
import Form from "./components/Form.vue";
import Tarefa from "./components/Tarefa.vue";
import ITarefa from "./interfaces/ITarefa"

export default defineComponent({
  name: "App",
  components: {
    BarraLateral,
    Form,
    Tarefa
  },
  data () {
    return {
      tarefas: [] as ITarefa[]
    }
  }
});
</script>

<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral />
    </div>
    <div class="column is-three-quarter">
      <Form />
      <div class="lista">
        <Tarefa />
      </div>
    </div>
  </main>
</template>


<style scoped>
.lista {
  padding: 0.5rem;

}
</style>
