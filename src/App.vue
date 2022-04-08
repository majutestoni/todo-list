<template>
  <main>
    <div class="esquerda">
      <BarraLateral />
      <div class="telaprincipal">
        <TelaPrincipal
          v-if="modoMostrarTodo == true"
          class="telaprincipal"
          :class="{ modoTodo: modoMostrarTodo }"
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
    mostrarAdicionarTodo() {
      this.modoMostrarTodo = !this.modoMostrarTodo;
      const body = document.getElementById('telaPrincipal') // iniciar teste utilizando assim
      //alterar display para block 
      // https://pt.stackoverflow.com/questions/481108/como-manipular-css-com-vue
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
.telaPrincipal {
  display: none;
}

.telaPrincipal.modoTodo {
  display: block;
}
</style>
