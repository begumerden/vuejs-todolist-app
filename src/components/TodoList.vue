<template>
  <div>
    <p>Completed Tasks: {{todoList.filter(todo => {return todo.done === true}).length}}</p>
    <p>Pending Tasks: {{todoList.filter(todo => {return todo.done === false}).length}}</p>
    <!--passing the data to the todo component to render the todo list-->
    <todo v-on:delete-todo-item="deleteTodoItem" v-for="todo in todoList" v-bind:todo="todo"></todo>
  </div>
</template>

<script type="text/javascript">

  import Todo from './Todo';

  export default {
    props: ['todoList'], // declaring the properties that will accept when using
    components: {
      Todo
    },
    methods: {
      deleteTodoItem(todo) {
        const todoIndex = this.todoList.indexOf(todo);
        this.todoList.splice(todoIndex, 1);
      }
    }
  };
</script>
<style scoped>
</style>
