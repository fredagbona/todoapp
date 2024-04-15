<template>
  <div>
    <AddTask @add-task="addTask"/>
    <TodoList :tasks="tasks" @toggle-task="toggleTask" />
  </div>
</template>
<script>
  import TodoList from './components/TodoList.vue';
  import AddTask from './components/AddTask.vue';
  export default {
    components: {
      TodoList,
      AddTask
    },
    data() {
      return {
        tasks: []
      }
    },
    methods: {
      addTask(newTask) {
        this.tasks.push({ name: newTask, completed: false });
      },
      toggleTask(index, checked) {
        this.tasks[index].completed = checked;
      }
    },
  }

</script>
<style>

</style>
