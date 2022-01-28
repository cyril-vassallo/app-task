<template>
  <div>
      <div @click="$emit('close-aside')" class="close">
        <i class="fas fa-times"></i>
      </div>
      <h2>Nouvelle tâche</h2>
      <form @submit="onSubmit" class="form">
      <div class="form-control text">
          <label for="text">Votre tâche:</label>
          <input v-model="text" type="text" id="text" name="text" placeholder="ex: Allez faire des courses"/>
      </div>
      <div class="form-control text">
          <label for="deadLine"> Heure limite:</label>
          <input v-model="deadLine" type="text" id="deadLine" name="deadLine" placeholder="ex: 14h"/>
      </div>
      <div class="form-control checkbox">
          <label for="reminder">Rappel :</label>
          <input v-model="reminder" type="checkbox" id="reminder" name="reminder"/>
      </div>
      <div>
        <button class="add" type="submit">Ajouter</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'Form',
  data () {
    return {
      text: '', 
      deadLine: '', 
      reminder: true
    }
  },
  methods: {
    onSubmit(e) {
      e.preventDefault()
      const task = {
        id: Math.floor(Math.random() * 1000),
        text: this.text,
        deadLine: this.deadLine,
        reminder: this.reminder
      }
      this.$emit('add-task', task);
      this.clear()
    },
    clear () {
      this.text = ''
      this.deadLine = ''
      this.reminder = true
      document.getElementById('aside').classList.add('hide')
    }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h2 {
    color: white;
    text-shadow: 2px 2px 2px black;
  }

  .form-control.text {
    display: flex;
    flex-direction: column;
  }

  .form-control.checkbox {
    display: flex;
    justify-content: center;
  }

  .form-control input {
    height:2rem;
    margin: auto;
    border-radius: 5px;
    border-color: rgb(3, 132, 207)
  }

  .form-control input:hover {
    border-color: rgb(51, 207, 3)
  }

  .form-control input:focus {
    border: 3px solide green ;
  }

.form-control label {
  color:white;
  font-weight: bold;
  margin: auto;
  padding: 1rem;
  text-align: left;
}


.fa-times {
  color:gray;
  border-radius: 50%;
  width: 15px;
  height: 15px;
}

.fa-times:hover {
  color:white;
}

.close {
  position: absolute;
  top:1rem;
  right: 1rem;
}


</style>
