<template>
  <div class="todo-card">
    <div class="main">
      <input type="checkbox" name="done" id="done">
      <label for="done">{{todo.title}}</label> 
    </div>
    <div class="buttons">
      <button>Изменить</button>
      <button v-on:click="$emit('delete-todo', todo.id)">Удалить</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoCard",

  props: {
    todo: {
      type: Object,
      required: true
    }
  }
}

</script>

<style>
  .todo-card {
    border: 2px solid black;
    border-radius: 5px;
    display: flex;
    align-items: flex-start;
    justify-content: center;
    flex-direction: column;
    height: 70px;
    width: 300px;
    padding: 0 10px;
  }
</style>