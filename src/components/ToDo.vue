<template>
  <div>
    <input type="text" v-model="tarefa.text">
    <button @click="adicionarTarefa">Add</button>

    <h2>Lista de Afazeres</h2>
    <ul class="lista">
      <li v-for="(item, index) in lista" :key="item" :class="{ok: item.realizada}">
        <input type="checkbox" @click="feito(index)">{{item.text}}
        <button @click="deletar(index)">Deletar</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'toDoList',
  data () {
    return {
      lista: [],
      tarefa: {
        text: '',
        realizada: false
      }
    }
  },
  methods: {
    adicionarTarefa () {
      let tarefa = {
        text: this.tarefa.text,
        realizada: false
      }
      this.lista.push(tarefa)
      this.tarefa.text = ''
    },
    feito (index) {
      var realizada = this.lista[index].realizada
      if(realizada === true) {
        this.lista[index].realizada = false
      }
      else{
        this.lista[index].realizada = true
      }
    },
    deletar (index) {
      this.lista.splice(index, 1)
    }
  }
}
</script>

<style>
.lista{
  list-style: none;
}
.ok{
  text-decoration: line-through;
}
</style>