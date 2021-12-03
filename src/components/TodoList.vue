// при итерации по массиву доступ к отдельному элементу через v-for
// чтоб передать элемент v-bind
// чтоб принять проп, создаем объект props
// чтоб передать значение в html оборачиваем в двойные кавычки - интерполяция
// чтоб поднять событие слушаем его по названию, в значение передаем слушатель

<template>
  <div>
    <ul>
      <TodoItem 
      v-for='(todo, i) in todos'
      v-bind:todo='todo'
      v-bind:index="i"
      v-bind:key="todo.id"
      v-on:remove-todo="handleDeleteBtnClick"
       />
    </ul>
  </div>
</template>

<script>
import TodoItem from '@/components/TodoItem.vue'
export default {
  props: ['todos'],
  components: {
    TodoItem
  } ,
  methods: {
    handleDeleteBtnClick(id) {
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