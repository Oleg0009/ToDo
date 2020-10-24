<template>
    <div class="add-to-do">
      <input type="text" v-model="title" placeholder="Add to do">
        <button class="add" 
        @click="addTodo">+</button>
    </div>
</template>

<script>

export default {
    data(){
        return{
            title:''
        }

    },
 
    methods: {
        addTodo() {
            if (this.title){
                let todo={
                    id: Date.now(),
                    title:this.title,
                    completed:false
                }
                this.$emit('add-todo',todo);
            }
           
        }
    },
}
</script>


<style scoped>
.add-to-do input{
    margin: 10px;
}
.add{
    color: white;
    font-weight: 700;
    font-size: 20px;
    border: none;
    background-color: red;
    width: 60px;
    height: 30px;
}

.add:focus{
    outline: none;
}
.add:hover{
    opacity: 0.7;
}
</style>