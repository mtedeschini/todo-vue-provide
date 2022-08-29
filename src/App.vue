<template>
  <div class="container mt-5">
    <tarea-app />
  </div>
</template>

<script>
import TareaApp from './components/TareaApp.vue'

export default {
  name: 'App',
  components: {
    TareaApp
  }
}
</script>

<style>
.container{
  max-width: 600px;
}

</style>

