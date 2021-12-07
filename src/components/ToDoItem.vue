<template>
  <div>
    <input type="checkbox" @click="$emit('feito', index)" />
    {{ tarefa }}
    <button @click="$emit('deletar', index)">Deletar</button>
  </div>
</template>

<script>
export default {
  name: "ToDoItem",
  props: {
    tarefa: { type: String },
    realizado: { type: Boolean },
    index: { type: Number },
  },
};
</script>

<style>
</style>