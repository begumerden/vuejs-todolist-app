<template>
  <div class='ui centered card'>

    <!-- show when not in editing mode.-->
    <div class="content" v-show="!isEditing">
      <div class='header'>
        {{ todo.title }}
      </div>
      <div class='meta'>
        {{ todo.project }}
      </div>
      <div class='extra content'>
          <span class='right floated edit icon' v-on:click="showForm">
          <i class='edit icon'></i>
        </span>
        <span class='right floated trash icon' v-on:click="deleteItem(todo)">
          <i class='trash icon'></i>
        </span>
      </div>
    </div>

    <!-- form is visible when we are in editing mode-->
    <div class="content" v-show="isEditing">
      <div class='ui form'>
        <div class='field'>
          <label>Title</label>
          <input type='text' v-model="todo.title">
        </div>
        <div class='field'>
          <label>Description</label>
          <input type='text' v-model="todo.description">
        </div>
        <div class='ui two button attached buttons'>
          <button class='ui basic blue button' v-on:click="hideForm">
            Close X
          </button>
        </div>
      </div>
    </div>

    <div class='ui bottom attached green basic button' v-show="!isEditing &&todo.done" disabled>
      Completed
    </div>
    <div class='ui bottom attached red basic button' v-on:click="completeItem(todo)" v-show="!isEditing && !todo.done">
      Pending
    </div>
  </div>
</template>

<script>
  export default {
    name: "Todo",
    props: ['todo'],
    data() {
      return {
        isEditing: false,
      };
    },
    methods: {
      showForm() {
        this.isEditing = true;
      },
      hideForm() {
        this.isEditing = false;
      },
      deleteItem(todo) {
        // emit an event delete-item to the parent TodoList Component and pass the current TodoItem to delete
        this.$emit('delete-item', todo);
      },
      completeItem(todo) {
        this.$emit('complete-item', todo);
      }
    }
  }
</script>

<style scoped>
  .ui.card {
    display: inline-block;
  }
</style>
