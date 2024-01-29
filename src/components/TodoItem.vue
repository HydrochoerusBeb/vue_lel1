<template lang="">
    <div :class="(completed ? 'green' : 'red') +  ' todo_item'" @click='handleChange' @dblclick='handleRemove'>
        <h2>{{title}}</h2>
        <p>{{completed}}</p>
        <p>{{id}}</p>   
    </div>
</template>
<script>
export default {
    props:[
        'id', 'title', 'completed'
    ],
    emits: ['handleRemove', 'handleChange'],
    methods: {
        handleRemove(){
            this.$emit('handleRemove', this.id)
        },
        handleChange(){
            this.$emit('handleChange', this.id)
        }
    },
}
</script>
<style >
    .red{
        background-color: red;
    }
    .green{
        background-color: green;
    }
</style>