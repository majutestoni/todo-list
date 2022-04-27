<template>
  <div class="box">
    <div>
      <AdicionarList @aoSalvarTodo="organizarLista($event)" />
    </div>
    <div>
      <ul class="lista">
        <li v-for="(todo, index) in todoList" :key="index">
          <div class="fleg">
            <input type="checkbox" name="" id="checkbox" />
            <label for="checkbox">{{ todo.description }}</label>
            <input v-show="editID === todo.id" type="text" />
          </div>
          <div class="icones">
            <ion-icon @click="excluir(index)" name="trash-outline"></ion-icon>
            <ion-icon @click="editar(todo.id)" name="create-outline"></ion-icon>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import AdicionarList from "./AdicionarList.vue";

class Item {
  id: number;
  description: string;

  constructor(id: number, description: string) {
    this.id = id;
    this.description = description;
  }
}

export default defineComponent({
  name: "TelaPrincipal",
  components: {
    AdicionarList,
  },

  data() {
    return {
      todoList: [] as Array<Item>,
      tarefaConcluida: false,
      editID: NaN,
      estiloBlock: {
        display: "block",
      },
      estiloNone: {
        display: "none",
      },
    };
  },

  methods: {
    organizarLista(evento: Array<Item>) {
      this.todoList = evento;
    },

    concluirTarefa(elemento: HTMLElement) {
      this.tarefaConcluida = !this.tarefaConcluida;

      if (this.tarefaConcluida == true) {
        this.estiloBlock.display = "none";
        this.estiloNone.display = "block";
      } else {
        this.estiloBlock.display = "block";
        this.estiloNone.display = "none";
      }
    },

    excluir(index: number) {
      console.log("teste");

      this.todoList.splice(index, 1);
    },

    editar(id: number) {
      //essa função ira editar uma string, porem só estou com o array

      if (this.editID === id) {
        this.editID = NaN;
        return;
      }

      this.editID = id;
    },
  },
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
  font-size: 16px;
  padding: 6px;
  display: flex;
  justify-content: space-between;
  padding-left: 15px;
  padding-right: 25px;
  color: rgb(59, 59, 59);
}

li:hover{
   background-color: rgba(227, 193, 255, 0.808);
}

.lista ion-icon {
  margin-top: 5px;
  cursor: pointer;
  margin-right: -5px;
}

.fleg {
  width: 94%;
  cursor: pointer;
}

.fleg label {
  margin-left: 15px;
  cursor: pointer;
}

.fleg input {
  display: none;
}

.fleg input + label:before {
  content: "";
  width: 18px;
  height: 18px;
  border-radius: 4px;
  background-color: rgb(252, 246, 255);
  border: 1px solid gray;
  display: inline-block;
  vertical-align: middle;
  margin-right: 8px;
  margin-left: -16px;
}

.fleg input:checked + label:before {
  background-image: url("data:image/svg+xml,%0A%3Csvg xmlns='http://www.w3.org/2000/svg' width='20' height='20' viewBox='0 0 10 10'%3E%3Cg class='nc-icon-wrapper' stroke-width='1' fill='%23555555'%3E%3Cpath fill='none' stroke='%23FFFFFF' stroke-linecap='round' stroke-linejoin='round' stroke-miterlimit='10' data-cap='butt' d='M2.83 4.72l1.58 1.58 2.83-2.83'/%3E%3C/g%3E%3C/svg%3E");
  background-color: rgba(135, 71, 170, 0.747);
  background-position: center;
  border: none;
  padding: 1px;
}

.icones {
  display: flex;
  width: 5%;
  justify-content: space-between;
  font-size: 18px;
}
</style>>
