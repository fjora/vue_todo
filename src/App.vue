<template>
  <div id="app">
    <h1 class="ui dividing centered header">Vue.js Todo App</h1>
      <div class="ui two column middle stackable grid">
        <div class='center aligned column'  style="position:fixed;">
          <p class="ui centered card">Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
          <p class="ui centered card">Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
          <create-todo v-on:create-todo="createTodo"></create-todo>
        </div>
        <div class="center aligned column" style="margin-left:50%;">
          <todo-list v-bind:todos="todos"></todo-list>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

import TodoList from './components/TodoList' 
import CreateTodo from './components/CreateTodo'
export default {
  components:{
    TodoList,
    CreateTodo,

  },
  data() {
    return {
      todos : [
      {
        title: 'Todo A',
        project: 'Project A',
        done: false
      },
      {
        title: 'Todo B',
        project: 'Project B',
        done: false
      },
      {
        title: 'Todo C',
        project: 'Project C',
        done: false
      },
      {
        title: 'Todo D',
        project: 'Project D',
        done: false
      },
    ]
    }
  },
  methods: {
    createTodo(newTodo) {
      this.todos.push(newTodo);
    },
  }
}
</script>

<style>

</style>
