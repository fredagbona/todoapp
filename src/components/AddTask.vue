<template>
  <div>
    <h2>Add Task</h2><br>
    <form @submit.prevent="addTask">
      <input name="task" v-model="newTask" placeholder="Task Name">
      <button  type="submit">Add Task</button>
    </form><br> <br>
  </div>
</template>

<script >
  export default {
    data() {
      return {
        newTask: '',
        tasks: [],
      }
    },
    methods: {
      addTask(){
        //console.log('Adding task:', this.newTask);
        if(this.newTask.trim() !== "") {
          this.$emit('add-task', this.newTask);
          this.newTask = '';

        }

      }
    }
  }
</script>

<style>

</style>