<template>
    <div class="todo-wrapper">
            <h2>To-Do List</h2>
                <AddTodo
                @add-todo="addTodo"
                ></AddTodo>
            <hr>
            <select v-model="filter">
                <option value="all">All</option>
                <option value="completed">Completed</option>
                <option value="not-completed">Not Completed</option>
            </select>

            <div v-if="loading"><Loader></Loader>  </div>
            <div class="todo-block" v-else-if="filteredTodos.length">
                <TodoItem 
                :key="todo.id"
                :index="index" 
                :todo="todo"
                @remove-todo="removeTodo" 
                v-for="(todo,index) of filteredTodos"></TodoItem>
            </div>
            <div v-else>
                  Empty
            </div> 
    </div>
</template>


<script>
import TodoItem from './Todo-Item';
import Loader from './Loader';
import AddTodo from './Add-to-do';

export default {

    data() {
        return { 
            todos:[],
            loading:true,
            filter:'all'
        }

    },
    components:{
        TodoItem,
        AddTodo,
        Loader
    },
    mounted() {
        fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
        .then(response => response.json())
        .then(json =>{ 
            setTimeout(()=>{
                this.loading = false;
                this.todos=json;
            },300)
        })
    },
    // watch: {
    //     filter(value){
    //         console.log(value)

    //     }
    // },
    computed:{
        filteredTodos() {
            if(this.filter=='all'){
                return this.todos;
            }
            else if(this.filter=='completed'){
                return this.todos.filter(
                    todo => todo.completed
                );
            }
            else{
               return this.todos.filter(
                    todo => !todo.completed
                ); 
            }
            
        }
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