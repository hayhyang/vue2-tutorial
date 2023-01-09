<template>
<div>
  <label for="checkbox">{{checked}}</label>
  <input id="checkbox" type="checkbox" v-model="checked"/>

  <label for="jack">jack</label>
  <input id="jack" value="jack" type="checkbox" v-model="checks"/>

  <label for="john">john</label>
  <input id="john" value="john" type="checkbox" v-model="checks"/>

  <label for="mike">mike</label>
  <input id="mike" value="mike" type="checkbox" v-model="checks"/>

  <label for="one">one</label>
  <input id="one" value="one" type="radio" v-model="picked"/>

  <label for="two">two</label>
  <input id="two" value="two" type="radio" v-model="picked"/>
  <p>{{checks}}</p>
  <p>picked: {{picked}}</p>
  <p>selected: {{selected}}</p>

  <select v-model="selected">
    <option>A</option>
    <option>B</option>
    <option>C</option>
  </select>
</div>
</template>

<script>
export default {
  name: 'CheckBox',
  component: {},
  data () {
    return {
      checked: true,
      checks: [],
      picked: '',
      selected: ''
    }
  },
  setup () {},
  created () {},
  mounted () {},
  unmounted () {},
  methods: {}
}
</script>

<style>

</style>
