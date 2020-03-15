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
        id: Number
    },
    methods: {
        removeTodo: function() {
            this.$emit('todo-remove', this.id)
        },

        onCancel: function() {
            this.$emit('deletion-canceled')
        }
    }
}
</script>