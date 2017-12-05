<template>
  <div>
    
    <todo v-on:un-complete-todo="unCompleteTodo" v-on:complete-todo="completeTodo" v-for="todo in todos" v-bind:todo="todo"></todo>
    <div class="ui basic modal">
        <div class="ui icon header">
          <i class="delete icon"></i>
          Delete ToDo
        </div>
        <div class="ui two column centered grid">
          <div class="column">
            <p>You are now trying to delete a ToDo option, are you sure?</p>
          </div>
        </div>
        <div class="actions">
          <div class="ui red basic cancel inverted button">
            <i class="remove icon"></i>
            No
          </div>
          <div class="ui green ok inverted button"  v-on:click="deleteTodo()">
            <i class="checkmark icon"></i>
            Yes
          </div>
        </div>
      </div>
  </div>
</template>

<script type = "text/javascript" >

import Todo from './Todo';

export default {
  props: ['todos'],
  components: {
    Todo,
  },
  methods: {
    deleteTodo(todo){
        const todoIndex = this.todos.indexOf(todo);
        this.todos.splice(todoIndex, 1);
    },
    completeTodo(todo) {
    const todoIndex = this.todos.indexOf(todo);
    this.todos[todoIndex].done = true;
    },
    unCompleteTodo(todo) {
    const todoIndex = this.todos.indexOf(todo);
    this.todos[todoIndex].done = false;
    },

  }
};
</script>
<style>
</style>