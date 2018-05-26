<template>
  <div>
    <p>Completed Tasks: {{todoList.filter(todo => {return todo.done === true}).length}}</p>
    <p>Pending Tasks: {{todoList.filter(todo => {return todo.done === false}).length}}</p>
    <!--passing the data to the todoComponent to render the todo list-->
    <todo v-on:delete-item="deleteItem" v-on:complete-item="completeItem"
          v-for="todo in todoList" v-bind:todo="todo" v-bind:key="todo.id"></todo>
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
      deleteItem(todo) {
        const todoIndex = this.todoList.indexOf(todo);
        this.todoList.splice(todoIndex, 1);
      },
      completeItem(todo) {
        const todoIndex = this.todoList.indexOf(todo);
        this.todoList[todoIndex].done = true;
      },
    }
  };
</script>
<style scoped>

</style>
