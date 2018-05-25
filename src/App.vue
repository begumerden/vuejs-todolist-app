<template>
  <div id="app">
    <img class="ui small centered image" src="./assets/logo.png">
    <h1 class="ui dividing centered header">Simple Todo List App</h1>

    <!--To render the component, we invoke it like an HTML element and passing data to component-->
    <div class="container">
      <new-todo v-on:add-item="addItem"/>
      <todo-list v-bind:todoList="todoList"/>
    </div>

  </div>
</template>

<script>
  //import HelloWorld from './components/HelloWorld'
  import TodoList from './components/TodoList'
  import NewTodo from './components/NewTodo'

  export default {
    name: 'App',
    components: {
      // HelloWorld,
      TodoList,
      NewTodo
    },
    data() {
      return {
        todoList: [{
          title: 'Todo 1',
          project: 'Project 1',
          done: false,
        }, {
          title: 'Todo 2',
          project: 'Project 2',
          done: true,
        }, {
          title: 'Todo 3',
          project: 'Project 3',
          done: false,
        }]
      };
    },
    methods: {
      addItem(newItem) {
        this.todoList.push(newItem);
      }
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
  .ui.container {
    overflow: auto;
    white-space: nowrap;
  }
</style>
