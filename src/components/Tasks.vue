<template>
  <div  class="tasks">
    <ul>
      <Task @toggle-reminder="$emit('toggle-reminder', task.id )"  @delete-task="$emit('delete-task' , task.id)" v-bind:key="task.id"  v-for="task in tasks" v-bind:task="task"/>
    </ul>
  </div>
</template>

<script>

import Task from './Task.vue'

export default {
  name: 'Tasks',
  components: {
    Task
  },
  props: ['tasks']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .tasks {
    margin: auto;
  }
</style>
