<template>
  <li @dblclick="$emit('toggle-reminder', task.id)" class="task">
    <div :class="[ task.reminder ?  'reminder': '' ]"></div>
    <div>
      {{ task.text }} - avant:  {{ task.deadLine }}  
    </div>
    <div @click="$emit('delete-task', task.id)">
      <i class="fas fa-times"></i>
    </div>
  </li>
</template>

<script>
export default {
  name: 'Task',
  props: ['task']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.task {
  max-width: 50%;
  display:flex;
  justify-content: space-between;
  margin: 1rem auto;
  padding: 1rem;
  background-color:whitesmoke;
  border: 1px solid rgb(189, 189, 189);
  border-radius: 3px;
  box-shadow: 2px 2px 2px gray;
  font-weight: bold;
}

li>div {
  margin: 5px;
}

.reminder {
  width: 15px;
  height: 15px;
  background-color: green;
  border-radius: 50px;
}

.fa-times {
  box-shadow: 1px 1px 2px black;
  border-radius: 50%;
  width: 15px;
  height: 15px;
}


</style>
