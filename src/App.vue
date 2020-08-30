<template>
  <section id="app">
    <TodoHeader />
    <TodoList :data="tasks"/>
  </section>
</template>

<script>
import tasks from './assets/scripts/data.js';
import TodoHeader from './components/TodoHeader';
import TodoList from './components/TodoList';

export default {
  name: 'App',
  components: {
    TodoHeader,
    TodoList
  },
  data() {
    return {
      tasks: tasks
    } 
  }
}
</script>

<style lang="scss">
body {
  background: #e7e7e7;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
