// если нужно динамически добавлять атрибут v-bind:атрибут
// передаем в фигурных скобках условие отображения или значение
// отлавливаем событие директивой v-on:имясобытия, внутрь бработчик
// поднятие стейта осуществяем через $emit в скобках имя события и параметр который будет доступен обработчику
// аналог propTypes тоже есть
<template>
  <li>
    <span v-bind:class="{done: todo.status}">
      <input type="checkbox" v-on:change="todo.status = !todo.status">
      <strong>{{index + 1}}</strong>
      {{todo.title}}
    </span>
    <button class="remove" v-on:click="$emit('remove-todo', todo.id)">&times;</button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    },
    index: {
      type: Number
    }
  }
}
</script>

<style scoped>
  li {
    border: 1px solid #ccc;
    display: flex;
    justify-content: space-between;
    padding: .5rem 2rem;
    margin-bottom: 1rem;
  }

  button {
    color: white;
    background-color: black;
    border: none;
  }

  input{
    margin-right: 1rem;
  }

  .done {
    text-decoration: line-through;
  }
</style>