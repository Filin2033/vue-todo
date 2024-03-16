<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="title">
    <button type="submit">Дабавить задачу</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: ''
    }
  },
  methods: {
    onSubmit() {
      console.log('Submit', this.title)
      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          completed: false
        }

        this.$emit('add-todo', newTodo)
        this.title = ''
      }
    }
  }
}
</script>

<style scoped>
  form {
    display: flex;
    justify-content: center;
    flex-wrap: column wrap;
    align-items:center;
    column-gap:30px;
  }

  input {
    width: 400px;
    height: 25px;
  }

  button {
    cursor: pointer;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2); 
  }
</style>