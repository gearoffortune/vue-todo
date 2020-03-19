<template>
    <div>
        <p>Editing</p>
        <input type="text" v-model="editableText">
        <button @click="onEdit">OK</button>
        <button @click="onCancel">Cancel</button>
    </div>
</template>

<script>
export default {
  props: {
    text: String,
    id: Number,
    isComplete: Boolean,
  },
  data() {
    return {
      editableText: '',
    };
  },
  methods: {
    onCancel() {
      this.$emit('editing-canceled');
    },
    onEdit() {
      this.$emit('todo-edited', { id: this.id, newText: this.editableText });
    },
  },
  beforeMount() {
    this.editableText = this.text;
  },
};
</script>
