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
            todos:[
                { id:1 , title: "Work", completed: false },
                { id:2 , title: "Study", completed: false },
                { id:3 , title: "English", completed: false }
            ]
        }

    },
    components:{
        TodoItem,
        AddTodo
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