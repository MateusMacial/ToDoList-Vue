<template>
  <div>
      <p>{{text}}</p>
  </div>
</template>

<script>
export default {
    name: 'ToDoItem',
    props: {
        text: {type: String},
        realizado: {type: Boolean}
    }
}
</script>

<style>

</style>