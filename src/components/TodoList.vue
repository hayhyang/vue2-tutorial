<template>
<div>
  <form v-on:submit.prevent="addTodo">
    <label for="new-todo">Add a todo</label>
    <input
        v-model="newTodo"
        type="text" id="new-todo"
        placeholder="E.g. Feed the cat"
    />
    <button>Add</button>
  </form>

  <ul>
    <li
        is="todo-item"
        v-for="(todo, index) in todos"
        :key="todo.id"
        :title="todo.title"
        v-on:remove="todos.splice(index, 1)"
    ></li>
  </ul>
</div>
</template>

<script>

import TodoItem from "@/components/Todo.vue";

export default {
  name: 'TodoList',
  components: {TodoItem},
  component: {},
  data () {
    return {
      newTodo: '',
      todos: [
        {
          id: 1,
          title: 'Do the dishes',
        },
        {
          id: 2,
          title: 'Take out the trash',
        },
        {
          id: 3,
          title: 'Mow the lawn'
        }
      ],
      nextTodoId: 4
    }
  },
  setup () {},
  created () {},
  mounted () {},
  unmounted () {},
  methods: {
    addTodo() {
      this.todos = [{id: this.nextTodoId++, title: this.newTodo}, ...this.todos]
      this.newTodo = ''
    }
  }
}
</script>

<style>

</style>\
