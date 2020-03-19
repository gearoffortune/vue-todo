<template>
    <div class="todo">
        <input @click="onChecked" type="checkbox">
        <p class="todo__text">{{text}}</p>
        <button @click="onEdit">edit</button>
        <button @click="onRemove">remove</button>
    </div>
</template>

<script>
export default {
  props: {
    text: String,
    timestamp: Number,
    id: Number,
    isComplete: Boolean,
  },
  data() {
    return {

    };
  },
  methods: {
    onChecked() {
      this.$emit('todo-checked', this.id);
    },
    onEdit() {
      this.$emit('modal-change', this.id);
    },
    onRemove() {
      this.$emit('modal-remove', this.id);
    },
  },
};
</script>

<style>
.todo {
    border: 1px solid black;
}
</style>
