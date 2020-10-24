<template>
  <div>
    <router-link to="/">Home link</router-link>
    <TodoList></TodoList>
  </div>
</template>
<script>
  import TodoList from '../components/Todo-List'

export default {
  name: 'App',
  components: {
    TodoList
  }
}
</script>