<template>
  <header>
    <h1>
      <img src="../assets/project.png" alt="logo">
    </h1>
    <button class="button" @click="alterarTema">
    {{textoButton}}
    </button>
  </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
 name: 'BarraLateral',
 emits: ['aoTemaAlterado'],
 data () {
  return {
    modoEscuroAtivo: false,
  }
 },
 computed: {
  textoButton() {
    if (this.modoEscuroAtivo) {
      return 'Ativar Modo Claro'
    }
    return 'Ativar Modo Noturno'
  }
 },
 methods: {
  alterarTema() {
    this.modoEscuroAtivo = !this.modoEscuroAtivo
    this.$emit('aoTemaAlterado', this.modoEscuroAtivo)
  }
 }
})
</script>

<style scoped>
header {
  background: #0d3b66;
  width: 100%;
  height: 100vh;
  padding: 1rem;
  text-align: center;
}

.button {
  width: 100%;
  margin-top: 0.6rem;
  border-radius: 1rem;
   box-shadow: 0 0 10px rgba(224, 221, 221, 0.534);
}

@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>