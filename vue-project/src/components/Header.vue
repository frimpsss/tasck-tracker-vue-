<template>
    <header>
        <h1>Time Tracker</h1>
        <Button @click="onClick()" :text="showAddTaskC ? 'close' : 'Add task'"
         :color="showAddTaskC ? 'red' : 'green'"
        @toggle-add="$emit('toogle-add')" />
    </header>
</template>

<script>
import Button from './Button.vue'
    export default{
    name: "Header",
    components: {
        Button
    },
    methods: {
        onClick(){
            this.$emit('toggle-add')
        }
    }, 
    props: {
        showAddTaskC: Boolean
    }
    
}
</script>


<style scoped>
    header{
        display: flex;
        justify-content: space-around;
        align-items: center;
        margin-bottom: 20px;
    }
</style>