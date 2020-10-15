<template>
  <div class="input">
    <input v-model="input" type="text" v-on:keyup.enter="addItem">
    <button type="button" v-on:click="addItem">Add</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      input: ''
    }
  },
  methods: {
    addItem() {
      // передаём данные обратно в родителя через встроенный метод vue $emit
      // 'add' - имя типа события и данные, в данном случаи объект
      this.$emit('add', {
        id: Date.now(),
        text: this.input,
        done: false
      });

      this.input = '';
    }
  }
}
</script>
