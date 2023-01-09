<template>
  <li>
    {{title}}
    <button v-on:click="$emit('remove')">remove</button>
  </li>
</template>

<script>
export default {
  name: 'TodoItem',
  props: {
    title: String,
  },
}
</script>
