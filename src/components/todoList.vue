<template>
  <div class="todoList">
    <div class="listHeader">
      <span></span>
      <h2>{{list.title}}</h2>
      <button v-on:click="$emit('delete-list', list.id)" class="deleteButton">&times;</button>
    </div>
    <select v-model="filter">
      <option value="all">all</option>
      <option value="completed">completed</option>
      <option value="not-completed">not completed</option>
    </select>
    <input type="search" v-model="search" placeholder="искать заметку" />
    <AddTodo @add-todo="addTodo" />
    <TodoCard 
      v-for="todo in searchTodo" :key="todo.id"
      v-bind:todo="todo" 
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
      search: "",
      filter: "all",
      todos: []
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

  computed: {
    searchTodo() {
      return this.todos.filter((todo) => {
        return todo.title.toLowerCase().includes(this.search.toLowerCase())
      })

      if (this.filter === "all") {
        return this.todos
      } 

      if (this.filter === "completed") {
        return this.todos.filter(t => t.done)
      }

      if (this.filter === "not-completed") {
        return this.todos.filter(t => !t.done)
      }
    },

  }
}
</script>

<style>
  .todoList {
    display: flex;
    flex-direction: column;
    border: 2px solid black;
    justify-content: center;
    border-radius: 5px;
    padding: 10px;
    width: 30%;
    margin-bottom: 15px;
  }

  .listHeader {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .todoList h2 {
    margin: 10px;
  }

  .deleteButton {
    font-size: 20px;
    border-radius: 5px;
    color: white;
    background: red;
    border: none;
  }

  input[type="search"] {
    margin: 10px 0;
  }

</style>