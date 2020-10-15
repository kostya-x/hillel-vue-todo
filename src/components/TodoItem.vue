<template>
  <div class="todo-item__content" v-bind:class="{'is-done':todo.done}">
    <span>{{todo.text}}</span>
    <button type="button" v-on:click="doneItem">+</button>
    <button type="button" v-on:click="deleteItem">del</button>
  </div>
</template>

<script>
export default {
  props:['todo'],
  methods: {
    doneItem() {
      this.$emit('toggle-done', this.todo.id);
    },
    deleteItem(){
      this.$emit('delete-item', this.todo.id);
    }
  }
}
</script>

<style lang="scss">
.is-done {
  text-decoration: line-through;
}
</style>