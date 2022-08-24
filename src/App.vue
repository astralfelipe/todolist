<template>
  <div id="app">
    <h1 class="formTitle d-flex justify-content-center m-0 pb-4">{{title}}</h1>
    <div class="formTarea d-flex justify-content-center  pb-3">
        <h4 class="pr-3">Tarea</h4>
        <input class="form-control pr-3"  ref="input" type="text" placeholder="Ingresa nueva tarea" v-model="tarea" @keyup.enter="agregaTarea">
        <button class="btnCrear mr-3 ml-3" @click="agregaTarea">Crear</button>
        <button class="btnLimpiar" @click="limpiarTarea">Limpiar</button>
    </div>
    <div class="listaTarea d-flex justify-content-center">
      <ol class="list-group">
        <li class="pt-2 font-weight-bold h5" v-for="todo in todos" :key="todo">
          {{ todo.text }}
        </li>
    </ol>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        title: 'Crear una nueva tarea',
        todos: [],
        tarea:'',
      }
  },
  methods: {
    agregaTarea: function () {

      if (this.tarea == '') {
        alert('El input está vacio')
      } else {
        this.todos.push({text: this.tarea});
        this.tarea = "";
        this.$refs.input.focus();
      }
  },
    limpiarTarea: function() {
      this.todos=[]
    },
  }
}
</script>

<style scoped>
  /* #app {
    font-size: 25px;
    font-family: "Calibri", sans-serif;
    color: darkblue;
    background: lightblue;
  } */

  * {
    color: #4C4C6D;
  }

  .formTitle {
    background-color: #FFE194;
    border-radius: 10px 10px 0 0;
    color: #4C4C6D;
  }

  .formTarea {
    background-color: #FFE194;
  }

  input {
    width: 20%;
    border-radius: 10px;
  }

  .btnCrear {
    border-radius: 10px;
    border: none;
    background-color: #B8DFD8;
    width: 100px;
  }

  .btnLimpiar {
    border-radius: 10px;
    border: none;
    background-color: #E8F6EF;
    width: 100px;
  }

  .listaTarea {
    background-color: #E8F6EF;
    border-radius: 0 0 10px 10px;
  }
</style>