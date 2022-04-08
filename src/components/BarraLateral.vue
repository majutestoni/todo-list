<template>
  <input type="checkbox" id="check" />
  <header>
    <label for="check">
      <ion-icon name="menu-outline" id="sidebar_btn"></ion-icon>
    </label>
    <div class="left">
      <h3>Todo <span>list</span></h3>
    </div>
  </header>
  <div class="sidebar">
    <center>
      <img src="../assets/logo.png" class="imagem" alt="" />
      <h2>Maria</h2>
    </center>
    <a href="#"
      ><ion-icon name="desktop-outline"></ion-icon><span>Alterar tema</span></a
    >
    <a href="#"
      ><ion-icon name="calendar-outline"></ion-icon><span>Calendario</span></a
    >
    <a href="#" @click="AdicionarTodo"
      ><ion-icon name="duplicate-outline"></ion-icon
      ><span>Adicionar todo</span></a
    >
  </div>
</template>
<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "BarraLateral",
  emits: ["aoAdicionarTodo"],
  data() {
    return {
      // imagem: '../assets/logo.png',
      modoAdicionarAtivo: false,
    };
  },

  methods: {
    AdicionarTodo() {
     // this.modoAdicionarAtivo = !this.modoAdicionarAtivo;
      this.$emit("aoAdicionarTodo", this.modoAdicionarAtivo)
      console.log('clicou')
    },
  },
});
</script>

<style >
header {
  position: fixed;
  background: rgb(68, 11, 116);
  padding: 20px;
  width: 100%;
  height: 30px;
}

.left h3 {
  color: #fff;
  margin: 0;
  text-transform: uppercase;
  font-size: 22px;
  float: right;
  margin-right: 60px;
}

.left span {
  color: rgb(48, 203, 241);
}

label #sidebar_btn {
  z-index: 1;
  position: fixed;
  left: 110px;
  color: #fff;
  font-size: 25px;
  margin: 5px 0;
  cursor: pointer;
  transition: 0.2s;
}

label #sidebar_btn:hover {
  color: rgb(48, 203, 241);
}

#check:checked ~ .sidebar {
  left: -190px;
}

#check:checked ~ .sidebar a span {
  display: none;
}

#check:checked ~ .sidebar a {
  font-size: 20px;
  margin-left: 170px;
  width: 80px;
}

#check {
  display: none;
}
.sidebar {
  position: fixed;
  width: 250px;
  height: 100%;
  margin-top: 70px;
  padding-top: 30px;
  left: 0;
  background: rgba(73, 74, 112, 0.555);
  transition: 0.5s;
  transition-property: left;
  backdrop-filter: blur(5.5px);
  -webkit-backdrop-filter: blur(5.5px);
}

.sidebar .imagem {
  width: 100px;
  height: 100px;
  border-radius: 100px;
}

.sidebar h2 {
  color: rgb(204, 204, 204);
  margin-top: 0;
  margin-bottom: 20px;
}

.sidebar a {
  color: #fff;
  display: block;
  width: 100%;
  line-height: 60px;
  text-decoration: none;
  padding-left: 40px;
  box-sizing: border-box;
  transition: 0.2s;
}

.sidebar a:hover {
  background: rgba(69, 11, 116, 0.808);
}

.sidebar ion-icon {
  padding-right: 10px;
}
</style>