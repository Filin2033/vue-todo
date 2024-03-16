<template>
  <li v-bind:class="todo.completed ? 'done' : 'undone'">
    <span v-bind:class="{done: todo.completed}">
      <input type="checkbox" 
      v-on:change="todo.completed = !todo.completed">
      <strong>{{index + 1}}</strong>
      {{todo.title | uppercase}}
    </span>
    <button class="rm" v-on:click="$emit('remove-todo', todo.id)">&times;</button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    },
    index: Number
  },
  filters: {
    uppercase(value) {
      return value.toUpperCase()
    }
  }
}
</script>

<style scoped>
  li {
    display: flex;
    align-items:center;
    column-gap:30px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    border: 1px solid #ccc;
    display: flex;
    justify-content: space-between;
    padding: .5rem 2rem;
    margin-bottom: 1rem;
    border-radius: 10px;
  }

  .undone {
    background-color: #baf5d4;
  }
  
  .done {
    background-color: #dc143c;
  }

  .rm {
    background: red;
    color: #fff;
    border-radius: 50%;
    width: 30px; 
    height: 30px;
    font-weight: bold;
    padding: 8px; 
    border: none; 
    cursor: pointer; 
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2); 
    transition: background-color 0.3s, box-shadow 0.3s, transform 0.3s;
  }
  
  .rm:hover {
    background: hsl(0, 70%, 50%);
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
    transform: translateY(2px);
  }

  input {
    margin-right: 1rem;
    cursor: pointer;
  }

  .done {
    text-decoration: line-through;
  }
</style>