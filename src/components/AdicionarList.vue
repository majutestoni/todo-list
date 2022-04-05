<template>
  <div class="adicionar" role="form">
    <input
      class="descricao"
      type="text"
      placeholder="Adicione seu todo"
      v-model="descricao"
      id="descricao"
      name="descricao"
    />
    <button class="adicionar_btn" @click="novoTodo" type="submit">Adicionar</button>
  </div>
</template>
<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "AdicionarList",
  emits: ["aoSalvarTodo"],
  data() {
    return {
      id: 0,
      descricao: "",
      listaTodo: [] as Array<string>,
    };
  },

  methods: {
    novoTodo() {
      this.listaTodo.push(this.descricao);
      this.$emit("aoSalvarTodo", this.listaTodo);
    },
  },
});
</script>
<style>
.descricao {
  margin-top: 80px;
  margin-left: 280px;
  width: 120vh;
  height: 5vh;
  border-radius: 6px;
  border: none;
  outline: none;
  padding: 4px;

}

.adicionar_btn{
    margin-left: 10px;
    height: 5vh;
    padding: 4px;
    border: none;
    padding: 4px;
    border-radius: 6px;
}
</style>
