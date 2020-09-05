<template>
  <div class="todoList">
    <h2>{{list.title}}</h2>
    <button v-on:click="$emit('delete-list', list.id)" class="deleteButton">&times;</button>
    <AddTodo @add-todo="addTodo" />
    <TodoCard 
      v-for="todo in todos"
      v-bind:todo="todo" :key="todo.i"
      v-on:delete-todo="deleteTodo"
    />
  </div>
</template>

<script>
import TodoCard from "@/components/todoCard"
import AddTodo from "@/components/addTodo"

export default {
  name: "TodoList",
  
  props: {
    list: {
      type: Object,
      required: true
    }
  },

  data() {
    return {
      todos: [
        {id:1, title: "123", done: false},
        {id:2, title: "4123", done: false},
        {id:3, title: "123as", done: false}
      ],     
    }
  },

  components: {
    TodoCard,
    AddTodo
  },

  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
    },

    addTodo(todo) {
      this.todos.unshift(todo)
    }
  },
}
</script>

<style>
  .todoList {
    border: 2px solid black;
    border-radius: 5px;
    padding: 10px;
    width: 30%;
  }

  .deleteButton {
    font-size: 20px;
    border-radius: 5px;
    color: white;
    background: red;
    border: none;
  }

</style>