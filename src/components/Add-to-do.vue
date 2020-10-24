<template>
    <div class="add-to-do">
      <input type="text" placeholder="Add to do">
        <button class="add" 
        @click="$emit('add-todo',todo)">+</button>
    </div>
</template>

<script>

export default {
    data(){
        return{

        }

    },
    components:{

    }
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
        border-radius: 20px;
        background-color: red;
        width: 30px;
        height: 30px;
}

.add:focus{
    outline: none;
}
.add:hover{
    opacity: 0.7;
}
</style>