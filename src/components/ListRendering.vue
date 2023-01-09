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

    <ol>
      <li v-for="number in evenNumbers" :key="number">{{number}}</li>
    </ol>
    <ol>
      <li v-for="number in even(number)" :key="number">{{number}}</li>
    </ol>

    <ol>
      <li v-for="n in 10" :key="n">{{n}}</li>
    </ol>

    <ul>
      <template v-for="(item) in items" >
        <li :key="item.message + 'm'">{{item.message}}</li>
        <li :key="item.message + 'd'" class="divider" role="presentation"></li>
      </template>
    </ul>
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
      },
      number: [
          1,2,3,4,5,6
      ]
    }
  },
  setup () {},
  created () {},
  mounted () {},
  unmounted () {},
  methods: {
    even (numbers) {
      return numbers.filter(n => n % 2 ===0)
    }
  },
  computed: {
    evenNumbers() {
      return this.number.filter(n => n % 2 === 0)
    }
  }
}
</script>

<style>

</style>
