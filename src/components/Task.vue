<template>
  <li @dblclick="$emit('toggle-reminder', task.id)" class="task">
    <div :class="[ task.reminder ?  'reminder-on': 'reminder-off' ]"></div>
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
  max-width: 100%;
  display:flex;
  justify-content: space-between;
  margin: 1rem auto;
  padding: 1rem;
  background-color:whitesmoke;
  border: 1px solid black;
  border-radius: 10px;
  box-shadow: 2px 2px 2px black;
  font-weight: bold;
}

.task:hover {
  background-color: #01459e;
  color: white;
  border-radius: 10px;
}

li>div {
  margin: 5px;
}

.reminder-on {
  min-width: 15px;
  min-height: 15px;
  width: 15px;
  height: 15px;
  background-color: rgb(0, 214, 0);
  border-radius: 50%;
  border: 1px solid gray;
}

.reminder-off {
  min-width: 15px;
  min-height: 15px;
  width: 15px;
  height: 15px;
  border-radius: 50%;
  background-color: white;
  border: 1px solid gray;
}


.fa-times {
  color: coral;
  background-color:whitesmoke;
  border-radius: 50%;
  width: 15px;
  height: 15px;
  border: 2px solid rgba(128, 128, 128, 0)
}

.fa-times:hover {
  border: 2px solid gray;
  box-shadow: 2px 2px 2px rgb(139, 139, 139);
}

</style>
