<template>
  <div class="container mt-5">
      <div class="row">
        <div class="col-lg-8 offset-lg-2">
          <input 
            class="form-control form-control-lg" 
            type="text" 
            placeholder="Ingresar tarea..."
            v-model="nombreTarea"
            v-on:keyup.enter="agregarTarea()"  
          />
          <br>
        </div>
      </div>
      <div class="col-lg-6 offset-lg-3">
        <div class="card" v-if="tareas.length === 0">
          <h6>No hay tareas para mostrar</h6>
        </div>
        <ul class="list-group" v-for="(tarea, index) in tareas" v-bind:key="index">
          <li class="list-group-item d-flex justify-content-between">
            <span class="cursor" v-bind:class="[tarea.estado === true ? 'text-success': '', 'cursor']" v-on:click="actualizarTarea(tarea, index)">
              <i v-bind:class="[tarea.estado === true ? 'fas fa-check-circle': 'far fa-circle']"></i>
            </span>
            <h6>
              {{ tarea.nombre }}
            </h6>
            <span class="cursor text-danger" v-on:click="eliminarTarea(index)">
              <i class="fas fa-trash-alt"></i>
            </span>   
          </li>
        </ul>
      </div>
  </div>
</template>

<script>
export default {
    data() {
        return{
            tareas: [],
            nombreTarea:""
            }
    },
    methods: {
      agregarTarea() {
        const tarea = {
          nombre: this.nombreTarea,
          estado: false
        }
          
          console.log(tarea);
          this.tareas.push(tarea);
          this.nombreTarea= "";
          console.log(this.tareas);
      },
      eliminarTarea(index) {
        this.tareas.splice(index,1);
      },
      actualizarTarea(tarea, index) {
        this.tareas[index].estado = !tarea.estado;
      }
    }

}
</script>

<style scoped>

  h6 {
    text-align: center;
    padding-top: 5px;
  }

  input {
    text-align: center;
  }

  .cursor {
    cursor: pointer;

  }
</style>