<template>
  <div>
    <h1>Todo List</h1><br>
    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        <input type="checkbox" :checked="task.completed" @change="toggleTask(index, $event.target.checked)">
        <label :class="{ 'completed': task.completed }">{{ task.name }}</label>
      </li>
    </ul>
  </div>
</template>

<script>
  export  default {
    data() {
      return {
        tasks: [],
      }
    },
    props: ['tasks'],
    methods: {
      toggleTask(index, checked) {
        this.$emit('toggle-task', index, checked);
      },
      saveTasks() {
        localStorage.setItem('tasks', JSON.stringify(this.tasks));
      },
      loadTasks() {
        const task = localStorage.getItem('tasks');
        //console.log('Loaded tasks from local storage:', this.tasks);
        if(task) {
          this.tasks = JSON.parse(task);
          //console.log('Tasks not loaded from local storage');

        }
      },
    },
    mounted() {
      this.loadTasks();
      //console.log('Tasks:', this.tasks);
    },
    watch: {
      tasks: {
        handler() {
          this.saveTasks();
        },
        deep: true,
      },
    },
  }
</script>

<style>
.completed {
  text-decoration: line-through;
}
li{
  list-style-type: none;
}
</style>