<template>
    <div class="todo-wrapper">
        <h2>To-Do List</h2>
        <AddTodo
        @add-todo="addTodo"
        ></AddTodo>
        <hr>
        <div class="todo-block" v-if="todos.length">
            <TodoItem 
            :key="todo.id" 
            :todo="todo"
            @remove-todo="removeTodo" 
             v-for="todo in todos"></TodoItem>
        </div>
        <div v-else>
           Empty
        </div>
    </div>
</template>


<script>
import TodoItem from './Todo-Item';
import AddTodo from './Add-to-do';

export default {

    data() {
        return { 
            todos:[]
        }

    },
    components:{
        TodoItem,
        AddTodo
    },
    mounted() {
        fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
        .then(response => response.json())
        .then(json => this.todos=json)
    },
    methods: {
        removeTodo(id){
            this.todos=this.todos.filter(t => t.id != id );
        },
        addTodo(todo) {
            console.log(todo)
            this.todos.push(todo);
        }
    },  
}
</script>


<style scoped>
    
.todo-block{
    display:flex;
    flex-direction: column;
}
    .todo-wrapper{
        text-align: center;
    }
</style>