<template>
  <div id="app">
    <todo-input v-on:add="addItem" />
    <ul>
      <li v-for="item in tasksList" :key="item.id">
        <todo-item 
          v-bind:todo="item"
          v-on:toggle-done="toggleDone"
          v-on:delete-item="deleteItem"
        />
      </li>
    </ul>
  </div>
</template>

<script>
import TodoInput from "./components/TodoInput";
import TodoItem from "./components/TodoItem";

export default {
  name: 'App',
  components: {
    TodoInput,
    TodoItem
  },
  data() {
    return {
      tasksList: []
    }
  },
  methods: {
    addItem(item) {
      this.tasksList.push(item);
    },
    toggleDone(id) {
      const index = this.tasksList.findIndex(e => e.id === id);
      this.tasksList[index].done = !this.tasksList[index].done;
      // this.tasksList.splice(index, 1, {
      //   ...this.tasksList[index],
      //   done: !this.tasksList[index].done
      // });
    },
    deleteItem(id) {
      const index = this.tasksList.findIndex(e => e.id === id);
      this.tasksList.splice(index, 1);
    }
  }
};
</script>

<style>
</style>
