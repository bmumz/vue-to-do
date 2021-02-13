<template>
  <div class="list">
    <div v-bind:key="toDo.id" v-for="toDo in toDos">
      <ToDoItem v-bind:toDo="toDo" v-on:del-toDo="$emit('del-toDo', toDo.id)" />
    </div>
  </div>
</template>

<script>
import ToDoItem from './ToDoItem';

export default {
  name: 'ToDoList',
  components: {
    ToDoItem,
  },
  props: ['toDos'],
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
