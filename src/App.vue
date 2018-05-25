<template>
  <div id="app">
    <img src="./assets/logo.png">
    <!--To render the component, we invoke it like an HTML element and passing data to component-->
    <div class='ui three column centered grid'>
      <todo-list v-bind:todoList="todoList"/>
      <new-todo v-on:add-todo-item="addTodoItem"/>
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
      addTodoItem(newItem) {
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
</style>
