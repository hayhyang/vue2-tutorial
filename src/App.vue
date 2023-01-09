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

<!--    interpolations-->
    <p>{{message}}</p>
    <p v-once>{{message}}</p>
    <p>{{rawHTML}}</p>
    <p v-html="rawHTML"></p>
    <button v-bind:disabled="isButtonDisabled">Button</button>
    <p>{{number + 1}}</p>
    <p>{{seen ? 'show': 'hide'}}</p>
    <p>{{new Date()}}</p>

<!--    Directives-->
    <p v-if="seen">show</p>
    <p v-else>hide</p>
    <form v-on:submit.prevent="onSubmit">
      <input type="text" v-model="message"/>
      <button type="submit">submit</button>
    </form>
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
      isButtonDisabled: false,
      todos: [
        { id: 1, text: 'Learn Javascript'},
        { id: 2, text: 'Learn Vue'},
        { id: 3, text: 'Learn React'}
      ],
      rawHTML: '<p>rawHTML</p>',
      number: 1
    }
  },
  methods: {
    reverseMessage:function () {
      this.message = this.message.split('').reverse().join('')
    },
    onSubmit: function () {
      console.log(this.message)
    }
  },
  created() {
    console.log("app created")
  },
  mounted() {
    console.log("app mounted")
  },
  updated() {
    console.log("app updated")
  },
  destroyed() {
    console.log("app destroyed")
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
