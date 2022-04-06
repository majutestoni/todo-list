<template>
  <main>
    <div class="esquerda">
      <BarraLateral  />
      <div class="telaprincipal">
        <TelaPrincipal @aoAdicionarTodo="adicionarTodo"/> 
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import BarraLateral from "./components/BarraLateral.vue";
import TelaPrincipal from "./components/TelaPrincipal.vue";
//mport AdicionarList from "./components/AdicionarList.vue"

export default defineComponent({
  name: "App",
  components: {
    BarraLateral,
    TelaPrincipal,
    //AdicionarList,
  },
});
</script>

<style>
main {
  background: url(assets/fundo.jpg) no-repeat;
  background-size: cover;
  background-position: center;
  height: 100vh;
  cursor: default;
}

.telaprincipal {

}
</style>
