<template>
  <div>
      <h2>Nouvelle tâche</h2>
      <form @submit="onSubmit" class="form">
      <div>
          <label for="text">Votre tâche:</label>
          <input v-model="text" type="text" id="text" name="text" placeholder="ex: Allez faire des courses"/>
          {{text}}
      </div>
      <div>
          <label for="deadLine"> Heure limite:</label>
          <input v-model="deadLine" type="text" id="deadLine" name="deadLine" placeholder="ex: 14h"/>
          {{ deadLine }}
      </div>
      <div>
          <label for="reminder">Rappel :</label>
          <input v-model="reminder" type="checkbox" id="reminder" name="reminder"/>
          {{ reminder }}
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
      reminder: false
    }
  },
  methods: {
    onSubmit(e) {
      e.preventDefault()
      alert('Please add a task')
    }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h2 {
    color: rgb(91, 144, 207);
    text-shadow: 2px 2px 2px black;
  }
</style>
