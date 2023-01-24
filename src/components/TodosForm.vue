<template>
  <form @submit="addToDo">
    <input type="text" v-model="title" name="title" placeholder="Input text" />
    <button class="bnt_submit" type="submit">Submit</button>
  </form>
</template>

<script>
import { v4 as uuidv4 } from 'uuid'

export default {
  name: 'TodosForm',
  data() {
    return {
      title: '',
    }
  },
  methods: {
    addToDo(event) {
      event.preventDefault()
      if (this.title) {
        const newToDoObject = {
          id: uuidv4(),
          title: this.title,
          userId: 1,
          completed: false,
        }

        this.$emit('add-todo-event', newToDoObject)
        this.title = ''
      }
    },
  },
}
</script>
