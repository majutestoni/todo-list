<template>
  <div class="box">
    <div >
      <AdicionarList @aoSalvarTodo="organizarLista($event)" />
    </div>
    <div>
      <ul class="lista">
        <li v-for="(todo, index) in todoList" :key="index" @click="trocarCor">
          {{ todo }}<ion-icon name="checkbox-outline"></ion-icon>
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
    };
  },

  methods: {
    organizarLista(evento: Array<string>) {
      this.todoList = evento;
    },

    trocarCor(){
      //Não está trocando a cor do check
      const cor = document.querySelector('ion-icon[name="checkbox-outline"]')
      cor?.setAttribute('style', 'color: blue')
      console.log('check')
    }
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

.lista ion-icon{
  margin-top: 5px;
  cursor: pointer;
}
</style>