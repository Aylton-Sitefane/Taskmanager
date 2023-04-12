<template>
    <div :class="[task.reminder ? 'reminder' : '', 'task']">
        <h3>{{ task.text }}
            <i @click="onDelete(task.id)" class="uil uil-trash"></i>
        </h3>
        <h3>{{ task.dia }}</h3>

    </div>
    
</template>

<script>
    export default{
        name:'Task',
        props:{
            task: Object,
        },
         methods:{
            onDelete(id){
                this.$emit('delete-task', id)
            },
        },
    }
</script>

<style scope>
    .task{
        background: #f4f4f4;
        margin: 5px;
        padding: 10px 20px;
        cursor: pointer;
    }

    .uil{
        color: red;
    }
    .task.reminder{
        border-left: 5px solid green;

    }

    .task h3{
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
</style>