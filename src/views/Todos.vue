<template>
  <div>
    <h2>Todo application</h2>
    <router-link to="/">Home</router-link>
    <hr>
    <AddTodo 
    @add-todo="addTodo" />
    <hr>
    <select v-model="filter">
      <option value="all">All</option>
      <option value="completed">Completed</option>
      <option value="not completed">Not Completed</option>
    </select>
    <TodoList 
      v-if="filteredTodos.length" 
      :todos="filteredTodos" 
      @remove-todo="removeTodo" />
    <p v-else>No todos!</p>
  </div>
</template>


<script>

import TodoList from '@/components/TodoList.vue'
import AddTodo from '@/components/AddTodo.vue'
export default {
  name: 'App',
  data() {
    return {
      todos: [
        {id: 1, title: 'Купить хлеб', completed: false},
        {id: 2, title: 'Купить молоко', completed: false},
        {id: 3, title: 'Купить гречку', completed: false}
      ],
      filter: 'all'
    }
  },
  computed: {
    filteredTodos() {
      if (this.filter === 'all') {
        return this.todos
      }

      if (this.filter === 'completed') {
        return this.todos.filter(t => t.completed)
      }

      if (this.filter === 'not completed') {
        return this.todos.filter(t => !t.completed)
      }
    }
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(t => t.id !== id)
    },
    addTodo(todo) {
      this.todos.push(todo)
    }
  },
  components: {
    TodoList,
    AddTodo
  }
}
</script>
