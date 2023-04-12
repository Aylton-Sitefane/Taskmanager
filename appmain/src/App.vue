<template>
  <div class="container">
    <Header title="Tarefas" />
    <Tasks @toggle-reminder="toggleReminder" @delete-task = "deleteTask" :tasks="tasks" />
  </div>
</template>

<script>

import Header from "./components/Header.vue"
import Tasks from "./components/Tasks"

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
  },
  data(){
    return {
      tasks: []
    }
  },
  methods:{
    deleteTask(id){
      if (confirm('Tem a certeza?')) {
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
      

    },
    toggleReminder(id){
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task)
    },
  },
  created(){
    this.tasks = [
      {
        id:1,
        text: 'Estudar para o teste',
        dia: '25 abril 2023',
        reminder: true,
      },
      {
        id:2,
        text: 'Reuniao familiar',
        dia:'23 abril 2023',
        reminder: true,
      }
      ,{
        id:3,
        text: 'Consulta no hospital',
        dia:'24 de abril de 2023',
        reminder: true,
      }
    ]
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

 * {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
 }

 body{
  font-family: 'Poppins', sans-serif;
 }
 .container{
  max-width: 500px;
  margin: 30px auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;

 }

 .btn{
  display: inline-block;
  background: #cdc7c7;
  color: #000;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
 }

 .btn:focus{
  outline: none;
 }

 .btn:hover{
   background-color: aqua;
 }
</style>
