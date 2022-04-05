<template>
  <div class="box">
    <div>
      <AdicionarList @aoSalvarTodo="organizarLista($event)" />
    </div>
    <div>
      <ul class="lista">
        <li v-for="(todo, index) in todoList" :key="index">{{ todo }}</li>
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
}
</style>