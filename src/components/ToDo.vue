<template>
  <div>
    <input type="text" v-model="tarefa.text" />
    <button @click="adicionarTarefa">Add</button>

    <h2>Lista de Afazeres</h2>
    <ToDoItem
      v-for="(item, index) in lista"
      :tarefa="item.text"
      :realizado="item.realizada"
      :index="index"
      :key="item.text"
      :class="{ ok: item.realizada }"
      @feito="feito"
      @deletar="deletar"
    >
    </ToDoItem>
  </div>
</template>

<script>
import ToDoItem from "./ToDoItem.vue";

export default {
  components: { ToDoItem },
  name: "toDoList",
  data() {
    return {
      lista: [],
      tarefa: {
        text: "",
        realizada: false,
      },
    };
  },
  methods: {
    adicionarTarefa() {
      let tarefa = {
        text: this.tarefa.text,
        realizada: false,
      };
      this.lista.push(tarefa);
      this.tarefa.text = "";
    },
    feito(index) {
      var realizada = this.lista[index].realizada;
      if (realizada === true) {
        this.lista[index].realizada = false;
      } else {
        this.lista[index].realizada = true;
      }
    },
    deletar(index) {
      this.lista.splice(index, 1);
    },
  },
};
</script>

<style>
.lista {
  list-style: none;
}
.ok {
  text-decoration: line-through;
}
</style>