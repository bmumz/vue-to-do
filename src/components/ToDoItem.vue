<template>
  <div>
    <div class="item-container">
      <input id="checkbox" type="checkbox" v-on:change="markComplete" />

      <h3 class="item" v-bind:class="{ 'is-complete': toDo.completed }">
        {{ toDo.item }}
      </h3>

      <button @click="$emit('del-toDo', toDo.id)" class="delete">X</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'toDoItem',
  props: ['toDo'],
  methods: {
    markComplete() {
      this.toDo.completed = !this.toDo.completed;
    },
  },
};
</script>

<style scoped>
.item-container {
  width: 35vw;
  display: flex;
  line-height: 2rem;
  align-items: center;
  padding: 1rem;
  margin: 1rem 0;
  border-left: 6px solid #b4b7b9;
  background: #eef2f3;
  background: linear-gradient(to right, #f1f1f1, #b4b7b9);
  border-radius: 0 1rem 1rem 0;
}

h3 {
  font-weight: 300;
  color: #444;
}
.item {
  margin: 0.5rem 2rem;
  width: 30vw;
}
.is-complete {
  text-decoration: line-through;
}

.delete {
  outline: none;
  background-color: #444;
  border: 1px solid #111;
  color: #eee;
  width: 1.5rem;
  height: 1.5rem;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 1rem;
}

.delete:hover,
.delete:active {
  background-color: #555;
}

.test {
  display: flex;
  justify-content: flex-end;
}
</style>
