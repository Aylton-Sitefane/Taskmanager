<template>
    <form @submit="onSubmit" class="form-control">
  <div >
    <label>Nome da tarefa</label>
    <input type="text" v-model="text" class="form-control input" id="nometarefa" placeholder="Descricao">
  </div>
  <div>
    <label for="diaehora"  class="form-label">Dia e hora</label>
    <input type="text"  v-model="dia" class="form-control input" id="diahora" placeholder="ex: DD HH">
  </div>
  <div class="mb-3 form-check">
    <input type="checkbox" v-model="reminder"  class="form-check-input" >
    <label class="form-check-label" for="exampleCheck1">Lembrar tarefa</label>
  </div>
  <button type="submit" class="btn btn-primary">Criar</button>
</form>
</template>

<script>
    export default {
        name: 'AddTask',
        data(){
            return {
                text: '',
                dia: '', 
                reminder: false
            }
        },
        methods: {
            onSubmit(e){
                e.preventDefault();

                if (!this.text) {
                    alert("Preencha o campo de tarefa")
                    return
                }

                const newTask = {
                    id: Math.floor(Math.random() * 1000000),
                    text: this.text,
                    dia: this.dia,
                    reminder: this.reminder,
                }

                this.$emit('add-task', newTask)

                this.text = ''
                this.dia = ''
                this.reminder = false
            }
        }
    }
</script>

<style>
    
</style>