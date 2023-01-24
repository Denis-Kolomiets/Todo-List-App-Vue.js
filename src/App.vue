<template>
  <div class="wrapper">
    <h4 class="title">Todo List App Vue.js</h4>
    <TodosForm @add-todo-event="addToDoItem" />
    <Todos v-bind:todos="todos" @delete-todo-event="deleteToDoItem" />
  </div>
</template>

<script>
import Todos from './components/Todos.vue'
import TodosForm from './components/TodosForm.vue'
export default {
  name: 'App',
  components: { Todos, TodosForm },
  data() {
    return {
      todos: [],
    }
  },
  methods: {
    addToDoItem(newToDoItem) {
      this.todos = [newToDoItem, ...this.todos]
    },
    deleteToDoItem(toDoId) {
      this.todos = this.todos.filter((item) => item.id !== toDoId)
    },
    async getData() {
      const res = await fetch(
        'https://jsonplaceholder.typicode.com/todos?_limit=3'
      )
      const finalRes = await res.json()
      this.todos = finalRes
    },
  },
  mounted() {
    this.getData()
  },
}
</script>
