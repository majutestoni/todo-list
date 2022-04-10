<template>
  <div class="box">
    <div>
      <AdicionarList @aoSalvarTodo="organizarLista($event)" />
    </div>
    <div>
      <ul class="lista">
        <li v-for="(todo, index) in todoList" :key="index">
          <button @click="concluirTarefa">teste</button>
          {{ todo }}<ion-icon name="checkbox-outline" :style="estilo"></ion-icon
          ><ion-icon name="square-outline" :style="estilo"></ion-icon>
        </li>
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import AdicionarList from "./AdicionarList.vue";

export default defineComponent({
  name: "TelaPrincipal",
  components: {
    AdicionarList,
  },

  data() {
    return {
      todoList: [] as Array<string>,
      tarefaConcluida: false,
      estilo: {
        display: 'block',
      },
    };
  },

  methods: {
    organizarLista(evento: Array<string>) {
      this.todoList = evento;
    },

    concluirTarefa() {
      const quadrado1 = document.getElementById("square-outline");
      const checkConcluido = document.getElementById("checkbox-outline");

//A troca de estilo no proprio componentes está funcionado, porem com o metodo não funcionar
//verificar setAttribute
      this.tarefaConcluida = !this.tarefaConcluida;
      if (this.tarefaConcluida == true) {
        quadrado1?.setAttribute("estilo", "display: none");
        checkConcluido?.setAttribute("estilo", "display: block");
        console.log("verdade");
      } else {
        quadrado1?.setAttribute("estilo", "display: block");
        checkConcluido?.setAttribute("estilo", "display: none");
        console.log("falso");
      }

      //square-outline
      //checkbox-outline
    },
  },
});
</script>
<style >
.lista {
  margin-top: 30px;
  margin-left: 280px;
  width: 120vh;
  list-style: none;
}

li {
  margin-top: 10px;
  background: rgba(243, 224, 253, 0.747);
  border-radius: 6px;
  font-size: 18px;
  padding: 5px;
  display: flex;
  justify-content: space-between;
  padding-left: 15px;
  padding-right: 25px;
  color: rgb(59, 59, 59);
}

.lista ion-icon {
  margin-top: 5px;
  cursor: pointer;
}
</style>