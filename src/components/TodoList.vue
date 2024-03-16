<template>
  <div>
    <ul>
      <Todoitems
      v-for="(todo, i) in todos"
      :key="todo.id"
      v-bind:todo="todo"
      v-bind:index="i"
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
    display: flex;
    flex-flow: column nowrap;
    column-gap:30px;
    list-style: none;
    margin: 0;
    padding: 0;
    border-radius: 10px;
  }
</style>