<template>
  <div id="app">
    <div>{{ message }}</div>
    <div v-bind:title="message">Hover your mouse over me for a few seconds
    to see my dynamically bound title!</div>
    <button v-on:click="reverseMessage">Reverse Message</button>
    <input v-model="message" />
    <div v-if="seen">Now you see me</div>
    <ul>
      <todo-item v-for="(todo) in todos" :key="todo.id" :todo="todo"/>
    </ul>
  </div>
</template>

<script>
import TodoItem from "@/components/Todo.vue";

export default {
  name: 'App',
  components: {
    TodoItem
  },
  data() {
    return {
      message: 'Hello World',
      seen: true,
      todos: [
        { id: 1, text: 'Learn Javascript'},
        { id: 2, text: 'Learn Vue'},
        { id: 3, text: 'Learn React'}
      ]
    }
  },
  methods: {
    reverseMessage:function () {
      this.message = this.message.split('').reverse().join('')
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
