
<template>
  <div id="app">
    <NewTodo @new-todo="onNewTodo"/>

    <div >
      <Todo v-for="todo in todos"
      :text="todo.text"
      :id="todo.id"
      :key="todo.id"
      :timestamp="todo.timestamp"
      :isComplete="todo.isComplete"
      @todo-checked="onCheckedTodo"
      @modal-change="createModalChange"
      @modal-remove="createModalDelete"
      />
      <DeleteModal v-if="isBeingRemoved"
      :id="idRemoved"
      @todo-remove="onTodoDeletion"
      @deletion-canceled="isBeingRemoved=false"
      />
      <EditModal v-if="isBeingEdited"
      :id="idChanged"
      :text="todos[idChanged].text"
      @editing-canceled="isBeingEdited=false"
      @todo-edited="onUpdatedTodo"
      />
    </div>
  </div>
</template>

<script>
import NewTodo from './NewTodo.vue';
import Todo from './Todo.vue';
import EditModal from './EditModal.vue';
import DeleteModal from './DeleteModal.vue';

export default {
  name: 'app',
  data() {
    return {
      todos: [],
      isBeingRemoved: false,
      isBeingEdited: false,
      idChanged: -1,
      idRemoved: -1,
    };
  },
  components: {
    NewTodo,
    Todo,
    EditModal,
    DeleteModal,
  },
  methods: {
    onNewTodo(newTodoText) {
      this.todos.push({
        text: newTodoText, timestamp: Date.now(), id: this.todos.length, isComplete: false,
      });
    },
    onCheckedTodo(todoIndexChanged) {
      this.todos[todoIndexChanged].isComplete = !this.todos[todoIndexChanged].isComplete;
    },
    onUpdatedTodo({ id, newText }) {
      this.todos[id] = {
        text: newText, timestamp: Date.now(), id, isComplete: false,
      };
      this.isBeingEdited = false;
    },
    onTodoDeletion(id) {
      this.todos = this.todos.filter((x) => x.id !== id);
      this.isBeingRemoved = false;
    },
    createModalChange(id) {
      this.idChanged = id;
      this.isBeingEdited = true;
    },
    createModalDelete(id) {
      this.idRemoved = id;
      this.isBeingRemoved = true;
    },
  },
};
</script>

<style>
</style>
