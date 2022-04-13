<template>
  <div class="box">
    <div>
      <AdicionarList @aoSalvarTodo="organizarLista($event)" />
    </div>
    <div>
      <ul class="lista">
        <li v-for="(todo, index) in todoList" :key="index">
          <div class="fleg">
            <ion-icon
              @click="concluirTarefa(index)"
              name="checkbox-outline"
              :style="estiloNone"
            ></ion-icon
            ><ion-icon
              @click="concluirTarefa(index)"
              name="square-outline"
              :style="estiloBlock"
            ></ion-icon>
            <p>{{ todo }}</p>
          </div>
          <div class="icones">
            <ion-icon name="trash-outline"></ion-icon>
            <ion-icon name="create-outline"></ion-icon>
          </div>
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
      estiloBlock: {
        display: "block",
      },
      estiloNone: {
        display: "none",
      },
    };
  },

  methods: {
    organizarLista(evento: Array<string>) {
      this.todoList = evento;
    },

    concluirTarefa(elemento: HTMLElement) {
      //A troca de estilo no proprio componentes está funcionado, porem com o metodo não funcionar
      //verificar setAttribute
      this.tarefaConcluida = !this.tarefaConcluida;

      if (this.tarefaConcluida == true) {
        this.estiloBlock.display = "none";
        this.estiloNone.display = "block";
      } else {
        this.estiloBlock.display = "block";
        this.estiloNone.display = "none";
      }
    },
  }
});
</script>
<style scoped>
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
  font-size: 19px;
  padding: 6px;
  display: flex;
  justify-content: space-between;
  padding-left: 15px;
  padding-right: 25px;
  color: rgb(59, 59, 59);
}

.lista ion-icon {
  margin-top: 5px;
  cursor: pointer;
  margin-right: -5px;
}

.fleg {
  display: flex;
  width: 94%;
}

.fleg p {
  margin-left: 15px;
}

.fleg ion-icon {
  font-size: 18px;
}

.icones {
  display: flex;
  width: 5%;
  justify-content: space-between;
  font-size: 18px;
}
</style>>
