<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="title">
    <button type="submit">Создать новый список</button>
  </form>
</template>

<script>
export default {
  name: "AddList",

  data() {
    return {
      title: ""
    }
  },

  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newList = {
          id: Date.now(),
          title: this.title,
        }

        this.$emit("add-list", newList)
        this.title = ""
      }
    }
  }
}
</script>

<style>

</style>