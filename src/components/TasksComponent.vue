<template>
    <div class="tasks">
        <template v-if="tasks.length">
            <Task v-for="(task, i) in tasks" :key="task.name" :task="task"
            @taskDeleted="$emit('taskDeleted', i)"
            @changeStatus="$emit('changeStatus', i)"
            ></Task>
        </template>
        <p v-else>Nada para fazer :)</p>
    </div>
</template>

<script>
    import Task from './TaskComponent.vue'
    export default{
        components: { Task },
        props:  { tasks: { type: Array, required: true } }
    } 
</script>

<style>
    .tasks{
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
    }

    .tasks .task{
        margin: 5px;
    }
</style> 