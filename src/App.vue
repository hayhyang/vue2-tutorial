<template>
  <div id="app">
    <button v-on:click="decrement">-</button>
    {{ count }}
    <button v-on:click="increment">+</button>
  </div>
</template>

<script>
import Vue from 'vue'
import Component from "vue-class-component";

@Component
export default class App extends Vue {
  count = 0

  increment() {
    this.count++
  }

  decrement() {
    this.count--
  }
}
</script>

<style>
</style>
