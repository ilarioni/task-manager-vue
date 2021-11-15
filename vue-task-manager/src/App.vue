<template>
  <div class="container">

    <Header 
      @toggle-add-task="toggleAddTask" 
      title="Task Manager"
      :showAddTask="showAddTask" 
      />

    <div v-show="showAddTask">
      <AddTask @add-task="addTask" />
    </div>
  
    <Tasks 
      @toggle-reminder="toggleReminder" 
      @delete-task="deleteTask" 
      :tasks="tasks"/>

  </div>
</template>

<script>
import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'
import AddTask from './components/AddTask.vue'

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
      showAddTask: false,
    }
  },
  methods: {
    toggleAddTask() {
      this.showAddTask = !this.showAddTask

    },
    addTask(task) {
      this.tasks = [...this.tasks, task]
    },

    // on click it shows alert window asking qeustion and if yes then it will delete the task
    deleteTask(id) {
      if (confirm('Are you sure?')) {
        this.tasks = this.tasks.filter((task) => task.id !==id ); // deleting task with the id 
      } 
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => 
      task.id === id ? { ...this.task, reminder: !task.reminder } : task)
    },
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
  }
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
</style>
