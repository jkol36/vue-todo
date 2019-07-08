<template>
  <div id="app">
    <Todos v-bind:todos="todos" />
  </div>
</template>

<script>
import Todos from './components/Todos.vue'

export default {
  name: 'app',
  components: {
    Todos
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
