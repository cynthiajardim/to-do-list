<template>
	<div id="app">
		<h1>To Do List ({{ dataHoje }})</h1>
        <addTask @taskAdded="addTasks"></addTask>
        <tasks :tasks="tasks" @taskDeleted="deleteTask" @changeStatus="changeTaskStatus"></tasks>
	</div>
</template>

<script>
import TaskComponent from './components/TasksComponent';
import NewTask from './components/NewTask.vue'

export default {
    components: {
        'tasks': TaskComponent,
        'addTask': NewTask
    },
    data() {
        return {
            tasks: [],
            dataHoje: (new Date(Date.now())).toLocaleDateString()
        }
    },
    methods: {
        addTasks(task){
            const sameName = t => t.name === task.name 
            //se fazendo um filtro para pegar elementos de mesmo nome, a variável fica vazia, isso significa que não há tarefas iguais
            const isNew = this.tasks.filter(sameName).length == 0
            if(isNew){
                this.tasks.push({
                    name: task.name,
                    pending: task.pending || true
                })
            }
        },
        deleteTask(i){
            this.tasks.splice(i, 1) 
        },
        changeTaskStatus(i){
            this.tasks[i].pending = !this.tasks[i].pending
        }
    }
}
</script>

<style>
	body {
		background: radial-gradient(circle, rgba(238,174,202,1) 0%, rgba(148,187,233,1) 100%); 
	}

	#app {
		display: flex;
		flex: 1;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 100vh;
	}

	#app h1 {
		margin-bottom: 5px;
		font-weight: 300;
		font-size: 3rem;
	}
</style>
