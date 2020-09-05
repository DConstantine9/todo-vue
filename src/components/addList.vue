<template>
  <form @submit.prevent="onSubmit">
    <button type="submit">Создать новый список</button>
  </form>
</template>

<script>
export default {
  name: "AddList",

  data() {
    return {
      title: "Новый список"
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
      }
    }
  }
}
</script>

<style>

</style>