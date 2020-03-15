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
        isComplete: Boolean
    },
    data: function() {
        return {
            editableText: ''
        }
    },
    methods: {
        onCancel: function() {
            this.$emit('editing-canceled')
        },
        onEdit: function() {
            this.$emit('todo-edited', {id: this.id, newText: this.editableText})
        }
    },
    beforeMount: function() {
        this.editableText = this.text
    }
}
</script>