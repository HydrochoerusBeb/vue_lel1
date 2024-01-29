<template lang="">
  <div>
    <AddTodo @addNewTodo='addNewTodo' ></AddTodo>
    <TodoList
    :todos='data'
    @removeTodo='removeTodo'
    @changeTodo='changeTodo'></TodoList>
  </div>
</template>

<script>
import AddTodo from './components/AddTodo.vue';
import TodoItem from './components/TodoItem.vue';
import TodoList from './components/TodoList.vue';
export default {
  components: {
    AddTodo, TodoItem, TodoList
  },
  data() {
    return {
      data: [
        {id: 1, title: 'Позавтракать', completed: true},
        {id: 2, title: 'Почистить огурцы', completed: false},
        {id: 3, title: 'Помыть кота', completed: true},
      ]
    }
  },
  methods: {
            removeTodo(id){
            this.data = this.data.filter((elem => elem.id !== id))
        },

        changeTodo(id){
            this.data = this.data.map(elem => {
            if (elem.id === id){
                elem.completed = !elem.completed
            }
            return elem
            })
        },
        addNewTodo(title){
            let newTodo = {
            id: Date.now(),
            completed: false,
            title:title,
            }

            this.data.push(newTodo)
        }
    },
}
</script>
<style>
.todo_item{
  display: flex;
  flex-direction: column;

  margin: 20px 170px;
  padding: 10px;

  outline: 2px solid black;
  box-shadow: 5px 5px 5px black;
}


.input_elem{
  display: flex;
  justify-content: center;
  margin: 20px 400px;
}

.input_elem > input{
  width: 100%;
  box-shadow: 5px 5px 5px black;
}
</style>