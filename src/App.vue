<template>
  <div id="app">
    <Header />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from './components/Todos.vue'
import Header from './components/layout/Header'

export default {
  name: 'app',
  components: {
    Todos,
    Header
  },
  data(){
    return {
      todos: [
        {
          id: '1',
          title: 'To do one',
          completed: false,
        },{
          id: '2',
          title: 'To do two',
          completed: true,
        },
        {
          id: '3',
          title: 'To do three',
          completed: false,
        }
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-kerning: auto;
}

html {
  font-family: sans-serif;
  -webkit-text-size-adjust: 100%;
}

body {
  margin: 0;
}
</style>
