<template>
  <div class="container">
    <Header title="Task Manager"/>
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks"/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
  },
  data() {
    return {
      tasks: []
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Doctor Appointment',
        day: 'February 22nd at 2:45pm',
        reminder: true
      },
      {
        id: 2,
        text: 'University Meeting',
        day: 'April 11th at 08:30am',
        reminder: true
      },
      {
        id: 3,
        text: 'Shopping',
        day: 'May 2nd 6:45pm',
        reminder: false
      }
    ] 
  },
  methods: {
    deleteTask(id) {
      if (confirm('Are you sure?')) {
        this.tasks = this.tasks.filter((task) => task.id !==id ); // deleting task with the id 
      } 
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => 
      task.id === id ? { ...task, reminder: !task.
      reminder } : task 
      )
    }
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 400px;
  border: 2px solid steelblue;
  padding: 20px;
  border-radius: 5px;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.95);
}

.btn-block {
  display: block;
  width: 100%;
}

/* 
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
*/ 
</style>
