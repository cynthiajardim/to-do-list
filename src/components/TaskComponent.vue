<template>
    <div class="task" :class="stateClass" @click="$emit('changeStatus', task)">
        <span class="close" @click="$emit('taskDeleted', task)">x</span>
        <p>{{task.name}}</p>
    </div>
</template>

<script>
    export default{
        props: {
            task: {type: Object, required: true}
        },
        computed: {
            stateClass() {
                return {
                    pending: this.task.pending,
                    done: !this.task.pending
                }
            }
        }
    } 
</script>

<style>
    .task{
        position: relative;
        box-sizing: border-box;
        width: 350px;
        height: 90px;
        padding: 10px;
        border-radius: 8px;
        font-size: 20px;
        font-weight: 300;
        cursor: pointer;
        user-select: none; 
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .pending{
        border-left: 8px solid #956379;
        background-color: #eb9bbe;
    }

    .done{
        color: #fff;
        border-left: 8px solid #95a2b2;
        background-color: #dbe1e8;
        opacity: 0.6;
        text-decoration: line-through;
    }

    .pending .close{
        background-color: #956379;
    }

    .done .close{
        background-color: #95a2b2;
    }

    .close{
        position: absolute;
        font-size: 0.9rem;
        right: 10px;
        top: 10px;
        height: 20px;
        width: 20px;
        border-radius: 10px;
        display: flex;
        justify-content: center;
    }

</style>