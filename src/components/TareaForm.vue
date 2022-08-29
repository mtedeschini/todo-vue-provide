<template>
    <div >
        <form @submit.prevent="agregarTarea">
            <input 
            class="form-control my-2"
            v-model.trim="itemTarea"
            type="text" 
            placeholder="Ingrese Tarea">
        <button class="btn btn-success w-100" type="submit">Agregar</button>
        </form>
    </div>
</template>

<script>
import { ref } from '@vue/reactivity'
import { inject } from '@vue/runtime-core'
export default {
    setup(){
        const itemTarea = ref('')
        const tareas = inject('tareas')

        const agregarTarea = () => {
            let tarea = {
                texto: itemTarea.value,
                estado: false,
                id: Date.now()
            }
            tareas.value.push(tarea)
            itemTarea.value = '';
        }
    
        return { itemTarea, agregarTarea }
    }

}
</script>

<style>

</style>