<template>
  <div>
    <ul>
      <Todoitems
      v-for="todo of todos"
      v-bind:todo="todo"
      v-on:remove-todo="removeTodo"
      />
    </ul>
  </div>
</template>

<script>
import Todoitems from '@/components/Todoitems'
export default {
  props: ['todos'],
  components: {
    Todoitems
  },
  methods: {
    removeTodo (id) {
      this.$emit('remove-todo', id)
    }
  }
}
</script>

<style scoped>
  ul {
    list-style: none;
    margin: 0;
    padding: 0;
  }
</style>