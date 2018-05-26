<template>
  <div class='ui basic content center aligned segment'>

    <button class='ui basic button icon' v-on:click="openForm()" v-show="!isCreating" data-tooltip="Add Task">
      <i class='plus icon'></i>
    </button>

    <div class='ui centered card' v-show="isCreating">
      <div class='content'>
        <div class='ui form'>
          <div class='field'>
            <label>Title</label>
            <input v-model="titleText" type='text' defaultValue="">
          </div>
          <div class='field'>
            <label>Description</label>
            <input v-model="projectText" type='text' defaultValue="">
          </div>
          <div class='ui two button attached buttons'>
            <button class='ui basic blue button' v-on:click="sendForm()">
              Create
            </button>
            <button class='ui basic red button' v-on:click="closeForm()">
              Cancel
            </button>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
  export default {
    name: "NewTodo",
    data() {
      return {
        titleText: '',
        projectText: '',
        isCreating: false,
      };
    },
    methods: {
      openForm() {
        this.isCreating = true;
      },
      closeForm() {
        this.isCreating = false;
      },
      sendForm() {
        if (this.titleText.length > 0 && this.projectText.length > 0) {
          const title = this.titleText;
          const project = this.projectText;
          this.$emit('add-item', {
            title,
            project,
            done: false,
          });
        }
        this.isCreating = false;
        this.projectText = '';
        this.titleText = '';
      }
    },
  }
</script>

<style scoped>

</style>
