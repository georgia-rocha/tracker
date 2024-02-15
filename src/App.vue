<script lang="ts">
import { defineComponent } from "vue";
import BarraLateral from "./components/BarraLateral.vue";
import Form from "./components/Form.vue";

export default defineComponent({
  name: "App",
  components: {
    BarraLateral,
    Form
  }
});
</script>

<template>
  <main class="columns is-gapless is-multiline is-flex">
    <div class="column is-one-quarter is-fullheight">
      <BarraLateral />
    </div>
    <div class="column is-three-quarter">
      <Form />
    </div>
  </main>
</template>


<style scoped>

</style>
