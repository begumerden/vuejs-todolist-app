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

  var LOCAL_STORAGE_KEY = 'vueTodoList';
  export default {
    name: 'App',
    components: {
      // HelloWorld,
      TodoList,
      NewTodo
    },
    watch: {
      todoList: {
        handler() {
          debugger;
          this.todoList.forEach(function (todo, index) {
            todo.id = index + 1
          });
          localStorage.setItem(LOCAL_STORAGE_KEY, JSON.stringify(this.todoList));
        },
        deep: true,
      },
    },
    data() {
      return {
        todoList: JSON.parse(localStorage.getItem(LOCAL_STORAGE_KEY) || '[]')
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
