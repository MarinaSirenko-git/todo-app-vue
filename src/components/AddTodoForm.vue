// как сделать контролируемый компонент - задать его изначальное состояние через v-model
// все что в data доступно через ключевое слово this
// если нужно заявить что обработчик отработал и передать данные this.$emit('имя которое слушаем', данные)
<template>
  <form v-on:submit.prevent="handleFormSubmit">
    <input type="text" v-model="title">
    <button>Add</button>
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
    handleFormSubmit(){
      if(this.title.trim()){
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
    border: 1px solid #ccc;
    display: flex;
    justify-content: space-between;
    padding: .5rem 2rem;
    margin-bottom: 1rem;
  }

  input {
    border: none;
    width: 100%;
  }

  button{
    color: white;
    background-color: black;
    border: none;
    height: 25px;
    width: 60px;
  }
</style>