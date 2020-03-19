<template>
    <div>
        <input v-model="inputText" type="text">
        <button @click="onAddTodo">Add</button>
    </div>
</template>

<script>
export default {
  data() {
    return {
      inputText: '',
    };
  },
  methods: {
    onAddTodo() {
      this.$emit('new-todo', this.inputText);
    },
  },
};
</script>
