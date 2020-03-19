<template>
    <div>
        <p>Remove?</p>
        <button @click="removeTodo">Yes</button>
        <button @click="onCancel">No</button>
    </div>
</template>

<script>
export default {
  props: {
    text: String,
    id: Number,
  },
  methods: {
    removeTodo() {
      this.$emit('todo-remove', this.id);
    },

    onCancel() {
      this.$emit('deletion-canceled');
    },
  },
};
</script>
