<template>
  <h1>My Todo App</h1>
  <form @submit.prevent="addTask">
    <label>New Task</label>
    <input v-model="newTask" name="newTask">
    <button>Add New Task</button>
  </form>
  <ul>
    <li v-for="task in tasks" :key="task.id">
       <h3 @click="toggleStatus(task)">
         {{task.content}}
       </h3>
    </li>
  </ul>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const newTask = ref('');
    const tasks = ref([]);

    function addTask() {
      tasks.value.push({
        id: Date.now(),
        status: false,
        content: newTask.value,
      });
      newTask.value = '';
    }

    function toggleStatus(task) {
      task.status = !task.status;      
    }

    return {
      newTask,
      tasks,
      addTask,
      toggleStatus,
    };
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
