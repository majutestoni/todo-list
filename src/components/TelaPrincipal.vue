<template>
  <div class="box">
    <div>
      <AdicionarList @aoSalvarTodo="organizarLista($event)" />
    </div>
    <ul class="lista">
      <li v-for="(todo, index) in todoList" :key="index">{{todo}}</li>
    </ul>
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
      this.todoList = evento
      console.log(evento)
    },
  },
});
</script>
<style >
.box{
    
}

.lista{
    margin-top: 100px;
    margin-left: 300px;
}
</style>