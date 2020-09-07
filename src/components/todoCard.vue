<template>
  <div class="todo-card">
    <div class="title">
      <input type="checkbox" name="done" id="done">
      {{todo.title}}
    </div>
    <div class="buttons">
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
    box-sizing: border-box;
    border-radius: 5px;
    display: flex;
    align-items: flex-start;
    justify-content: center;
    flex-direction: column;
    height: 70px;
    padding-left: 10px;
    width: 99%;
    margin-bottom: 10px;
  }
</style>