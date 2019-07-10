<template>
  <div id="app">
    <Header />
    <Addtodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from './components/Todos.vue'
import Header from './components/layout/Header'
import Addtodo from './components/Addtodo'
import axios from 'axios'

export default {
  name: 'app',
  components: {
    Todos,
    Header,
    Addtodo
  },
  data(){
    return {
      todos: []
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
    },
  },
  created() {
      axios.get('https://jsonplaceholder.typicode.com/todos')
      .then(res => this.todos = res.data)
      .catch(err => console.log(err))

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

  .btn {
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;

  }
  .btn:hover {
    background: #666;
  }
</style>
