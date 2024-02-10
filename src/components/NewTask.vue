<template>
    <div class="new-task">
        <input type="text" v-model="name" @keydown.enter="add" placeholder="Nova Tarefa">
        <button @click="add">+</button>
    </div>
</template>
<script>
    export default {
        data(){
            return {
                name: ''
            }
        },
        methods: {
            add(){
                this.$emit('taskAdded', {name: this.name})
                this.name = ''
            }
        }
    }
</script>

<style>
    .new-task input{
        width: 300px;
        height: 30px;
        border-radius: 5px 0px 0px 5px;
        border: none;
    }

    .new-task button {
        border-radius: 0px 5px 5px 0px;
        border: none;
        width: 25px;
        height: 32px;
    }
</style>