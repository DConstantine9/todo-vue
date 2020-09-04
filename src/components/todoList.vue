<template>
  <div>
    <h2>TodoList</h2>
    <AddTodo @add-todo="addTodo" />
    <select v-model="filter">
      <option value="all">all</option>
      <option value="completed">completed</option>
      <option value="not-completed">not completed</option>
    </select>
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
  /* props: ["todos"], */

  data() {
    return {
      todos: [
        {id:1, title: "123", done: false},
        {id:2, title: "4123", done: false},
        {id:3, title: "123as", done: false}
      ],
      filter: "all"
    }
  },

  components: {
    TodoCard,
    AddTodo
  },

  methods: {
    deleteTodo(id) {
      this.$emit("delete-todo", id)
    },

    addTodo(todo) {
      this.todos.unshift(todo)
    }
  },

  /* watch: {
    filter(value)
  } */
}
</script>

<style>

</style>