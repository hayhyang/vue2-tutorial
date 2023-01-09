<template>
  <div>
    <ul>
      <li v-for="(item, i) in items" :key="i">{{parentMessage}} - {{item.message}} - {{i}}</li>
    </ul>

    <ol>
      <li v-for="(value, i) in object" :key="i">{{value}}</li>
    </ol>
    <ol>
      <li v-for="(value,name, i) in object" :key="i">{{i+1}}) {{name}} : {{value}}</li>
    </ol>
  </div>
</template>

<script>
export default {
  name: 'ListRendering',
  component: {},
  data () {
    return {
      parentMessage: 'Parent',
      items: [
        {message: 'Foo'},
        {message: 'Bar'},
      ],
      object: {
        title: 'How to do lists in Vue',
        author: 'Jane Doe',
        publishedAt: '2016-04-10'
      }
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
