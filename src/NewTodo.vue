<template>
    <div>
        <input v-model="inputText" type="text">
        <button @click="onAddTodo">Add</button>
    </div>
</template>

<script>
export default {
    data: function(){
        return {
            inputText: ''
        }
    },
    methods: {
        onAddTodo: function(){
            this.$emit('new-todo', this.inputText);
        }
    }
}
</script>
