<template>
  <label class="check">
    <input type="checkbox" />
    <span class="checkmark" @click="buttonClicked(todo)"></span>
  </label>
  <span>{{ todo.title }}</span>
  <button
    :disabled="!todo.completed"
    class="btn_delete"
    @click="$emit('delete-todo-event', todo.id)"
  >
    X
  </button>
</template>

<script>
export default {
  name: 'Todo',
  components: {},
  props: ['todo'],
  methods: {
    buttonClicked(todo) {
      todo.completed = !todo.completed
    },
  },
}
</script>
