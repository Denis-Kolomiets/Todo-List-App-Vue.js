<template>
  <div class="empty" v-if="!todos.length">Todo list empty!</div>
  <ul class="todos">
    <li class="todo" v-for="todo in todos" :key="todo.id">
      <Todo
        v-bind:todo="todo"
        @delete-todo-event="$emit('delete-todo-event', todo.id)"
      />
    </li>
  </ul>
</template>

<script>
import Todo from './Todo.vue'
export default {
  name: 'Todos',
  components: {
    Todo,
  },
  props: ['todos'],
}
</script>
