<template>
    <div class="header">
      <h1>
        Toutes les tâches du {{ today }}
      </h1>
    </div>
</template>


<script>

export default {
  name: 'Header',
  props: ['today']
}

</script>


<style scoped>
  .header {
    padding: 3rem ;
    color: rgb(0, 110, 161);
  }

</style>
