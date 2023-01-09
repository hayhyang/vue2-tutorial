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
  <!--  computed properties and watchers-->
    <p>{{reversedMessage}}</p>

<!--    watchers-->
    <p>Ask a yes/no question</p>
    <input v-model="question" />
    <p>{{answer}}</p>
  <!--  class and style bindings-->
    <div class="static" :class="classObject2">Object Syntax</div>
    <div :class="[activeClass, errorClass]">Array Syntax</div>
    <div :class="[isActive ? activeClass : '', errorClass]">ternary expression</div>
    <ClassComponent class="baz boo" :class="{active: isActive}"/>
    <div :style="{display: ['flex', 'block']}">multiple values</div>
<!--    Conditional Rendering-->
    <div v-if="seen">v-if</div>
    <div v-else>v-else</div>

    <div v-if="Math.random() > 0.5">v-else</div>
    <div v-else>v-else show</div>
<!--    controlling reusable elements with key-->

  </div>


</template>

<script>
import TodoItem from "@/components/Todo.vue";
import _ from 'lodash'
import axios from 'axios'
import ClassComponent from "@/components/ClassComponent.vue";

export default {
  name: 'App',
  components: {
    ClassComponent,
    TodoItem
  },
  data() {
    return {
      loginType: 'username',
      message: 'Hello World',
      seen: true,
      isButtonDisabled: false,
      todos: [
        { id: 1, text: 'Learn Javascript'},
        { id: 2, text: 'Learn Vue'},
        { id: 3, text: 'Learn React'}
      ],
      rawHTML: '<p>rawHTML</p>',
      number: 1,
      question: '',
      answer: 'I cannot give you an answer until you ask a question!',
      isActive: true,
      hasError: false,
      classObject: {
        active: true, 'text-danger': false
      },
      activeClass: 'active',
      errorClass: 'text-danger'
    }
  },
  methods: {
    reverseMessage:function () {
      this.message = this.message.split('').reverse().join('')
    },
    onSubmit: function () {
      console.log(this.message)
    },
    getAnswer: function () {
      if(this.question.indexOf('?') === -1) {
        this.answer = 'Questions usually contain a question mark.'
        return
      }
      this.answer = 'Thinking...'

      axios.get('https://yesno.wtf/api').then((response) => this.answer = response.data.answer).catch(error => this.answer = 'error' + error)
    },
    toggleHandler: function () {
      // if(this.loginType === 'username') this.loginType = 'email'
      this.loginType = 'email'
    }
  },
  computed: {
      reversedMessage: function (){
        return this.message.split('').reverse().join('')
      },
    classObject2: function () {
        return {
          active: this.isActive,
          'text-danger': this.hasError
        }
    }
  },
  watch: {
    question: function () {
      this.answer = 'Wating for you to stop typing'
      this.debouncedGetAnswer()
    }
  },
  created() {
    console.log("app created")
    this.debouncedGetAnswer = _.debounce(this.getAnswer, 500)
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
.text-danger {
  color: red
}
.active {
  color: blue
}
</style>
