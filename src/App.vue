<template>
  <div id="app">
    <header>
     <Header/>
    </header>
    <main>
      <Form/>
      <Tasks :tasks="tasks" @toggle-reminder="toggleReminder" @delete-task="deleteTask"/>
    </main>
    <div class="background">
      <img alt="background" src="./assets/background.jpg"/>
    </div>
  </div>
</template>

<script>

import Header from './components/Header.vue'
import Form from './components/Form.vue'
import Tasks from './components/Tasks.vue'

export default {
  name: 'App',
  components: {
    Header,
    Form,
    Tasks
  },
   data(){
    return  {
      tasks : []
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Faire les courses',
        deadLine: '12h',
        reminder: true 
      },
      {
        id: 2, 
        text: 'Ranger ma chambre',
        deadLine: '16h',
        reminder: true 
      },
      {
        id: 3,
        text: 'Faire une machine à laver',
        deadLine: '19h',
        reminder: false 
      }
    ]
  },
  methods: {
    deleteTask(id) {
      if(confirm('Voulez vous suprimer cette tâche')){
        this.tasks = this.tasks.filter((task)=> task.id != id)
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map(task => task.id === id ? { ...task, reminder: !task.reminder} : task ) 
    }
  },
  emits: ['toggle-reminder', 'delete-task']
}
</script>

<style>
#app {
  position: relative;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.background {
  width: 100%;
  height: 80vh;
  position: absolute;
  top:0;
  left:0;
  border-radius:10px;
  border: 1px solid rgb(211, 211, 211);
  z-index: -10;

}

.background>img {
  width: 100%;
  height: 100%;

}

</style>
