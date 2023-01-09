<template>
  <button v-on:click="clickHandler">You clicked me {{count}} times.</button>
</template>

<script>
export default {
  name: 'ButtonCounter',
  component: {},
  data () {
    return {
      count: 0
    }
  },
  setup () {},
  created () {},
  mounted () {},
  unmounted () {},
  methods: {
    clickHandler() {
      this.count++
    }
  }
}
</script>

<style>

</style>
