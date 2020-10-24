<template>
    <div class="todo-item">
         <p :class="{ done: todo.completed }">
             <input type="checkbox" @change=" todo.completed =! todo.completed ">
             {{index+1}}
             {{todo.title | upperCase}}
        </p>
        <button class="remove" 
        @click="$emit('remove-todo',todo.id)">-</button>
    </div>
</template>


<script>

export default {
    props: {
        todo:{
            type: Object,
            required:true
        },
        index:Number
    },
    filters:{
        upperCase(value){
            return value.toUpperCase();
        }
    }
}
</script>

<style scoped>
.todo-item{
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom:1px black solid;
}
.remove{
    color: white;
    font-weight: 700;
     border: none;
    font-size: 20px;
    background-color: red;
    width: 60px;
    height: 30px;
}
.remove:focus{
    outline: none;
}
.remove:hover{
    opacity: 0.7;
}
.done{
    text-decoration: line-through;
}
    
</style>