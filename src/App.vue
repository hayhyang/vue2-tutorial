<template>
  <div id="app">
    <div>{{ message }}</div>
    <div v-bind:title="message">Hover your mouse over me for a few seconds
    to see my dynamically bound title!</div>
    <div v-if="seen">Now you see me</div>
    <ul>
      <li v-for="(todo, i) in todos" :key="i">{{todo.text}}</li>
    </ul>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {

  },
  data() {
    return {
      message: 'Hello World' + new Date().toLocaleString(),
      seen: true,
      todos: [
        {text: 'Learn Javascript'},
        {text: 'Learn Vue'},
        {text: 'Learn React'}
      ]
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
