<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="title">
    <button type="submit">Добавить</button>
  </form>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    }
  },

  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          done: false
        }

        this.$emit("add-todo", newTodo)
        this.title = ""
      }
    }
  }
}
</script>

<style>
  form {
    margin-bottom: 15px;
  }
</style>