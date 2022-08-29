<template>
    <h1 class="text-center">App Tareas</h1>
    <tarea-form />
    <tarea-item v-for="tarea in tareasArray" :key="tarea.id" :tarea="tarea"/>
    <div v-if="tareasArray.length === 0" class="alert alert-dark mt-3 text-center">Sin tareas pendientes 🥰</div>
    <p>{{tareasArray}}</p>
</template>

<script>
import { provide, ref, watchEffect } from 'vue'
import TareaForm from './TareaForm.vue'
import TareaItem from './TareaItem.vue'
export default {
  components: { TareaItem, TareaForm },
  setup(){
      const tareasArray = ref([])
      const ur = ""

      provide('tareas', tareasArray)

    if(localStorage.getItem('tasks')){
        tareasArray.value = JSON.parse(localStorage.getItem('tasks'))
    }

        //como useEffect
      watchEffect(() => {
          localStorage.setItem('tasks', JSON.stringify(tareasArray.value))
      })

      return { tareasArray }
  }

}
</script>

<style>

</style>