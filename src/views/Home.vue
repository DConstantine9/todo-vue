<template>
  <div>
    <h1>todo</h1>
    <TodoList 
      v-bind:todos="todos" 
      @delete-todo="deleteTodo" 
    />
  </div>
</template>

<script>
import TodoList from "@/components/todoList"

export default {
  components: {
    TodoList,
  },
  
 /*  data() {
    return {
      todos: [
        {id:1, title: "123"},
        {id:2, title: "4123"},
        {id:3, title: "123as"}
      ]
    } 
  },*/

  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
    }
  }
}
</script>
  
<style>
.todo {
  border: 1px solid black;
}
</style>
