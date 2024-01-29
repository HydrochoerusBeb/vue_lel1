<template lang="">
    <div>
        <TodoItem v-for="(todo, index) in todos" :key="index"
        :id='todo.id'
        :title='todo.title'
        :completed='todo.completed'
        @handleChange='handleChange'
        @handleRemove='handleRemove'
        ></TodoItem>
    </div>
</template>
<script>
import TodoItem from './TodoItem.vue';
export default {
    props:{todos: Array, },
    components: {
        TodoItem
    },
    emits: ['handleChange', 'handleRemove'],
    methods:{
        handleChange(id){
            this.$emit('changeTodo', id)
        },
        handleRemove(id){
            this.$emit('removeTodo', id)
            // console.log(id)
        },
       
    },
    data() {
        return {
            
        }
    },
    
}
</script>
<style>
    
</style>