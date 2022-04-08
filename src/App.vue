<template>
  <main>
    <div class="esquerda">
      <BarraLateral />
      <div>
        <TelaPrincipal
         id="teste"
         class="telaTodo"
          @aoAdicionarTodo="mostrarAdicionarTodo"
        />
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
  emits: ["aoMostrarTodo"],
  components: {
    BarraLateral,
    TelaPrincipal,
    //AdicionarList,
  },

  data() {
    return {
      modoMostrarTodo: false,
    };
  },

  methods: {
    //Recebido da barra lateral
    mostrarAdicionarTodo() {
      //Realizar troca de display none para block
      console.log('clicou')
      //está clicando
      this.$emit("aoMostrarTodo", this.modoMostrarTodo);
      const telaPrincipal = document.getElementById('text')
      //não está alterando
      telaPrincipal?.setAttribute('style', 'display: block');
    },
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

.telaTodo {
  display: none;
}

</style>
