<template>
  <div id="app">
    <header>
     <Header :today="today"/>
    </header>
    <main>
      <aside id="aside" class="hide">
        <Form @add-task="addTask"  @close-aside="show"/>
      </aside> 
      <section class="section">
          <button @click="show" class="add">{{ isDisplayed ? 'Annuler':'Ajouter une tâche'}}</button>
          <Tasks :tasks="tasks" @toggle-reminder="toggleReminder" @delete-task="deleteTask"/>
      </section>
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
      tasks : [],
      limit : 5,
      isDisplayed : false,
      days: ["Lundi", "Mardi", "Mercredi", "Jeudi", "vendredi", "Samedi", "dimanche"],
      today: ''
    }
  },
  created() {
    const date =  new Date()
    this.today = this.days[date.getDay()],
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
    },
    addTask (task) {
      if(task.text && task.deadLine) {
        if(this.tasks.length < this.limit ) {
          this.tasks = [...this.tasks, task]
        } else {
          alert(`Vous avez atteint la limite de ${this.limit} tâches journalières. Vous ne pouvez plus en ajouter.`)
        }
      } else {
        alert(`Aucune tâche ajoutée !`)
      } 
      this.isDisplayed = false;
    },
    show () {
      const asideEl = document.getElementById('aside')
      this.isDisplayed = asideEl.classList.contains('hide') ? true : false
      this.isDisplayed ?  asideEl.classList.remove('hide') : asideEl.classList.add('hide')
    } 
  },
  emits: ['toggle-reminder', 'delete-task', 'close-aside']
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
  overflow: hidden;
  height: 95vh;
  border-radius: 10px
}

main {
  display: flex;
}

.background {
  width: 100%;
  height: 100vh;
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

#aside {
  align-items: start;
  padding: 3rem;
  position: absolute;
  top:0;
  height:100vh;
  background-color: rgba(0, 0, 0, 0.897);
  box-shadow: 5px 0px 5px gray;
}

.hide {
  display: none;
}

.section {
  margin:auto;
}

button.add {
  border: 1px solide black;
  min-width: 10rem;
  height:3rem;
  color: white;
  font-weight: bold;
  border-radius: 10px;
  background-color: green;
}


button.add:hover {
  color: green;
  border-color: green;
  background-color: white;
}


</style>
