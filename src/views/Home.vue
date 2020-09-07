<template>
  <div class="main">
    <h1>todo</h1>
    <AddList @add-list="addList" />
    <TodoList 
      v-for="list in lists" :key="list.id"
      v-bind:list="list" 
      v-on:delete-list="deleteList"
    />
  </div>
</template>

<script>
import TodoList from "@/components/todoList"
import AddList from "@/components/addList"


export default {
  components: {
    TodoList,
    AddList
  },
  
  data() {
    return {
      filter: "all",
      lists: [
        {id: 1, title: "Список дел"},
      ]
    } 
  },

  methods: {
    
    deleteList(id) {
      this.lists = this.lists.filter(list => list.id !== id)
    },

    addList(list) {
      this.lists.unshift(list)
    }
  },

  computed: {
    filterTodos() {
      if (this.filter === "all") {
        return this.todos
      } else if (this.filter === "completed") {
        return this.todos.filter(t => t.done)
      } else {
        return this.todos.filter(t => !t.done)
      }
    }
  }
}
</script>
  
<style>
.main {
  display: flex;
  flex-direction: column;
  align-items: center;
}


.todo {
  border: 1px solid black;
}

input[type="checkbox"],
button, 
select {
  cursor: pointer;
  outline:none;
}


</style>
