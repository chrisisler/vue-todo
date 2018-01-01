<template>
  <div id='app'>
    <h1>First Vue Todo App</h1>

    <input placeholder='New Task' @keyup.enter='newTodo'/>

    <ul id='todos'>
      <li v-for='todo in todos'>
        {{ todo.task }}
        -
        <span v-if='todo.done'> Completed </span>
        <span v-else> Active </span>

        <button @click='deleteTodo(todo)'>Delete</button>
      </li>
    </ul>

  </div>
</template>

<script>
export default {
  methods: {
    deleteTodo(todo) {
      const index = this.todos.indexOf(todo)
      this.todos.splice(index, 1)
    },
    newTodo(event) {
      const task = event.target.value
      this.todos.push({ task, done: false })
    }
  },
  data: () => ({
    // Array { task: String, done: Boolean }
    todos: []
  })
}
</script>

<style>
</style>
