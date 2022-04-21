<template>
  <div class="fundo">
    <div class="adicionar" role="form">
      <input
        class="descricao"
        type="text"
        placeholder="Adicione seu todo"
        v-model="description"
        name="descricao"
      />
      <button class="adicionar_btn" @click="novoTodo" type="submit">+</button>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent } from "vue";

class Item {
  static itemCount = 0;
  public description;
  public id: number;

  constructor(description="") {
    Item.itemCount++;
    this.id = Item.itemCount;
    this.description = description;
  }
}

export default defineComponent({
  name: "AdicionarList",
  emits: ["aoSalvarTodo"],
  data() {
    return {
      description: "",
      listaTodo: [] as Array<Item>,
    };
  },

  methods: {
    novoTodo() {
      this.listaTodo.push(new Item(this.description));
      this.$emit("aoSalvarTodo", this.listaTodo);
      this.description = "";
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
  font-size: 20px;
}

.adicionar_btn {
  margin-left: 10px;
  height: 5vh;
  width: 5vh;
  padding: 4px;
  border: none;
  padding: 6px;
  border-radius: 100%;
  background-color: rgb(42, 188, 224);
  color: #fff;
  font-size: 18px;
  cursor: pointer;
  transition: 0.2s;
}

.adicionar_btn:hover {
  background-color: rgb(46, 138, 161);
}
</style>
