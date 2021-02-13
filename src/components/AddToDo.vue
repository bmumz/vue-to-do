<template>
  <div>
    <form @submit.prevent="addToDo" class="form">
      <input
        type="text"
        v-model="item"
        name="item"
        placeholder="Add to do..."
        class="add-to-do"
      /><input
        type="submit"
        value="Submit"
        class="button"
        @click="handleItem(item)"
      />
    </form>
  </div>
</template>

<script>
import { v4 as uuid } from 'uuid';

export default {
  name: 'AddToDo',
  data() {
    return {
      item: '',
    };
  },
  methods: {
    addToDo() {
      const newItem = {
        id: uuid(),
        item: this.item,
        completed: false,
      };
      this.$emit('add-toDo', newItem);
    },
  },
};
</script>

<style scoped>
.form {
  display: flex;
  height: 2rem;
  width: 35vw;
}

.add-to-do {
  width: 75%;
  padding: 0.5rem;
  text-transform: uppercase;
  letter-spacing: 2px;
}
</style>
