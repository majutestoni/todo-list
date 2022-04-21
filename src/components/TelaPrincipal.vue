<template>
  <div class="box">
    <div>
      <AdicionarList @aoSalvarTodo="organizarLista($event)" />
    </div>
    <div>
      <ul class="lista">
        <li v-for="(todo, index) in todoList" :key="index">
          <div class="fleg">
            <input type="checkbox" class="concluir" name="" id="" />
           
            <p>{{ todo.description }}</p>
           
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

.icones {
  display: flex;
  width: 5%;
  justify-content: space-between;
  font-size: 18px;
}

.concluir {
  position: relative;
  width: 1.5em;
  height: 1.5em;
  color: black;
  border: 1px solid gray;
  border-radius: 4px;
  appearance: none;
  outline: 0;
  cursor: pointer;
  transition: 175ms cubic-bezier(0.1, 0.1, 0.25, 1);
}
.concluir::before {
  position: absolute;
  content: '';
  display: block;
  top: 2px;
  left: 7px;
  width: 8px;
  height: 14px;
  border-style: solid;
  border-color: white;
  border-width: 0 2px 2px 0;
  transform: rotate(45deg);
  opacity: 0;
}

.concluir:checked {
  color: white;
  border-color: green;
  background: green;
}
input[type="checkbox"]::before {
  opacity: 1;
}

label::before {
  clip-path: polygon(0 0, 100% 0, 100% 100%, 0 100%);
}


label {
  position: relative;
  cursor: pointer;
  font-size: 1.5em;
  font-weight: 600;
  padding: 0 0.25em 0;
  user-select: none;
}
label::before {
  position: absolute;
  content: attr(data-content);
  color: lightgray;
  clip-path: polygon(0 0, 0 0, 0% 100%, 0 100%);
  text-decoration: line-through;
  text-decoration-thickness: 3px;
  text-decoration-color: black;
  transition: clip-path 200ms cubic-bezier(0.25, 0.46, 0.45, 0.94);
}
</style>>
