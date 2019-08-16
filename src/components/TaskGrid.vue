<template>

    <div class="task-grid">
        <template v-if="tasks.length > 0">
          <Task v-for="task in tasks" :key="task.name" 
          @removeTask="remove" :task="task"></Task>  
        </template>
        <p v-else class="no-tasks"> Sem Nenhuma atividade!</p>
    </div>

</template>
    
<script>
    import Task from './Task.vue';
    export default {
        components: { Task },
        props: {
            tasks: {type: Array, required: true}
        },
        methods: {
            remove(task) {
                this.$emit("removeTask", task);
            }
        }
    };
</script>
<style >

.task-grid {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
}

.task-grid .task {
    margin: 10px;
}

.no-task {
    color: #AAA;
    font-size: 1.7rem;
}
</style>