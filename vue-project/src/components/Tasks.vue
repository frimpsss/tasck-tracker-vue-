<template>
    <div v-for="task in tasks">
        <Task 
        @toggle-rem = "$emit('toggle-rem', task.id)"
        @delete-task="$emit('delete-task', task.id)" 
        :task='task'/>
    </div>
</template>

<script>
    import Task from './Task.vue'

    export default{
        name: "Tasks",
        props: {
            tasks: Array
        },
        components: {
            Task,
        },
        
    }
</script>