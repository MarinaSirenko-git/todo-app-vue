// ко всему что возвращается в data обращаемся через this
// методы жизненного цикла тоже есть

<template>
  <div id="app">
    <h1>Todo List</h1>
    <hr>
    <AddTodoForm
    v-on:add-todo="handleFormSubmit" 
    />
    <TodoList 
      v-bind:todos="todos"
      v-on:remove-todo="handleDeleteBtnClick" 
    />
  </div>
</template>

<script>

import TodoList from '@/components/TodoList'
import AddTodoForm from '@/components/AddTodoForm'


export default {
  name: 'App',
  data() {
    return {
      todos: []
    }
  },
  async mounted() {
    const res = await fetch('https://jsonplaceholder.typicode.com/todos')
    if (!res.ok) throw new Error(`Ошибка: ${res.status}`)
    const todoArr = await res.json()
    this.todos = todoArr
  },
  components: {
    TodoList,
    AddTodoForm
  },
  methods: {
    handleDeleteBtnClick(id) {
      this.todos = this.todos.filter((item) => item.id !== id)
    },
    handleFormSubmit(data) {
      this.todos.push(data)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
