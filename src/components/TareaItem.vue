<template>
    <div class="alert alert-warning mt-3 d-flex justify-content-between align-items-center" > 
        <div class="d-inline">
            <i 
                @click="editar(tarea.id)"
                role="button" 
                :class=" tarea.estado ? 'far fa-check-circle mx-1 text-success d-inline' : 'far fa-circle mx-1 text-success d-inline'"
            ></i>        
            <p :class="tarea.estado ? 'tachado m-0 d-inline' : 'm-0 d-inline'">{{tarea.texto}}</p>
        </div>
            <div>
                <i v-if="tarea.estado"
                @click="editar(tarea.id)"
                role="button" 
                class="fa-solid fa-undo-alt  mx-1 text-warning"
                ></i>        

                <i
                @click="eliminar(tarea.id)"
                role="button" 
                class="fa-solid fa-ban  mx-1 text-danger"
                ></i>
            </div>

            <!--<i class="fa-solid fa-rotate-left fa-lg"></i>-->
    </div>
</template>

<script>
import { inject } from '@vue/runtime-core'
export default {
    props: {
        tarea:{
            type: Object,
            required: true
        }
    },
    setup(){
        const tareas = inject('tareas')
        const eliminar = id => {
            tareas.value = tareas.value.filter(item => item.id != id)
        }
        const editar = id => {
            tareas.value = tareas.value.map(item =>{
                if(item.id === id){
                    item.estado = !item.estado 
                }
                return item
            })
        }
        
        return { eliminar, editar }
    }

}
</script>

<style scoped>

.tachado{
    text-decoration: line-through;
}

</style>