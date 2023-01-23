<script>
let id = 0

export default {
  data() {
    return {
      newTodo: '',
      todos: [
        { id: id++, text: 'Fill car with petrol'},
        { id: id++, text: 'Get milk and eggs'},
        { id: id++, text: 'Take dogs for a walk'}
      ]
    }
  },
  methods: {
    addTodo() {
      this.todos.push({id: id++, text: this.newTodo})
      this.newTodo = ''
    },
    removeTodo(todo) {
      this.todos = this.todos.filter((object) => object !== todo)
    }
  }
}
</script>

<template>
  <form @submit.prevent>
  <input v-model="newTodo" placeholder="Type your 'to do' here"/>
  <button @click="addTodo">Add "to do"</button>
  </form>
  <ul>
  <li v-for="todo in todos" :key="todo.id">{{ todo.text }}
  <button @click="removeTodo(todo)">x</button></li>
  </ul>

</template>