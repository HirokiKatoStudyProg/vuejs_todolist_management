<template>
  <div class="hello">
    <form v-on:submit.prevent>
      <input type="text" v-model="newItem">
        <button v-on:click="addItem">
          Add
        </button>
      <ul>
        <li v-for="(todo, index) in todos" :key='index'>
          <input type="checkbox" v-model="todo.isDone">
          <span v-bind:class="{ done: todo.isDone}">{{ todo.item }}</span>
          <button v-on:click="deleteItem(index)">delete</button>
        </li>
      </ul>
    </form>
  </div>
</template>

<script>
export default {
  name: 'TaskList',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      newItem: '',
      todos: []
    }
  },
  methods: {
    addItem: function (e) {
      if (!this.newItem) return
      var todo = {
        item: this.newItem,
        isDone: false
      }

      this.todos.push(todo)
      this.newItem = ''
    },
    deleteItem: function (index) {
      this.todos.splice(index, 1)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h2 {
  font-weight: normal;
}
ul {
  list-style: none;
}
li > span.done {
  text-decoration: line-through;
}
</style>
