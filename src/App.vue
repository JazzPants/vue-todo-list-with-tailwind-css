<script>
let id = 0

export default {
  data() {
    return {
      newTodo: '',
      hideCompleted: false,
      todos: [
        { id: id++, text: 'Fill car with petrol', done: true},
        { id: id++, text: 'Get milk and eggs', done: false},
        { id: id++, text: 'Take dogs for a walk', done: true}
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
  },
  computed: {
    filteredTodos() {

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
  <li v-if="!hideCompleted" v-for="todo in todos" :key="todo.id">
    <input type="checkbox" v-model="todo.done">
    <span>{{ todo.text }} </span>
  <button @click="removeTodo(todo)">x</button>
  </li>
  <li v-if="hideCompleted" v-for="todo in filteredTodos" :key="todo.id">
    <input type="checkbox" v-model="todo.done">
    <span>{{ todo.text }} </span>
  <button @click="removeTodo(todo)">x</button>
  </li>
  </ul>

</template>