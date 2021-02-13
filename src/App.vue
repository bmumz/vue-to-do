<template>
  <div id="app">
    <Header />
    <AddToDo v-on:add-toDo="addToDo" />
    <ToDoList v-bind:toDos="toDos" v-on:del-toDo="deleteToDo" />
  </div>
</template>

<script>
// imports
import AddToDo from './components/AddToDo';
import ToDoList from './components/ToDoList';
import Header from './components/layout/Header';

export default {
  name: 'App',
  components: {
    AddToDo,
    ToDoList,
    Header,
  },
  data() {
    return {
      toDos: [],
    };
  },
  mounted() {
    if (localStorage.toDos) {
      this.toDos = JSON.parse(localStorage.toDos);
    }
  },
  watch: {
    toDos(newToDo) {
      localStorage.toDos = JSON.stringify(newToDo);
    },
  },

  methods: {
    deleteToDo(id) {
      this.toDos = this.toDos.filter((toDo) => toDo.id !== id);
    },
    addToDo(newItem) {
      this.toDos = [...this.toDos, newItem];
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
.button {
  width: 25%;
  background-color: #333;
  color: #eee;
  text-transform: uppercase;
  letter-spacing: 2px;
  padding: 0.5rem;
}

.button:hover,
.button:active {
  background: #555;
}
</style>
