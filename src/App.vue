<template>
  <div id="app">
    <Header />
    <ToDoList v-bind:toDos="toDos" v-on:del-toDo="deleteToDo" />
  </div>
</template>

<script>
// imports
import ToDoList from './components/ToDoList';
import Header from './components/layout/Header';

export default {
  name: 'App',
  components: {
    ToDoList,
    Header,
  },
  data() {
    return {
      toDos: [
        { id: 1, item: 'Wash dishes', completed: false },
        { id: 2, item: 'Brush Reya', completed: false },
        { id: 3, item: 'Do laundry', completed: false },
        { id: 4, item: 'Make dinner', completed: false },
        { id: 5, item: 'Clean', completed: false },
      ],
    };
  },
  methods: {
    deleteToDo(id) {
      this.toDos = this.toDos.filter((toDo) => toDo.id !== id);
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  height: 100vh;
  font-family: Arial, Arial, Helvetica, sans-serif;
  line-height: 1.4;
  display: flex;
  justify-content: center;
  margin-top: 10rem;
  background-color: #eee;
}
</style>
