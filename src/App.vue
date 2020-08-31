<template>
  <section id="app">
    <TodoHeader />
    <TodoList :data="tasks"/>
    <div class="statistics">
      <p id="complete"><strong>Completed:</strong> {{ getCompletedTasks() }} / {{ tasks.length }}</p>
      <p id="limit"><strong>Limit:</strong> {{tasks.length}} / {{ limit }}</p>
    </div>
    
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
      tasks: tasks,
      limit: 5
    } 
  },
  methods: {
    getCompletedTasks() {
      let completed = 0;
      this.tasks.forEach(task => { if (task.isDone) completed++; })

      return completed;
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
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 50vw;
  margin: 0 auto;

  > * {
    width: 100%;
  }

  #limit {
    // margin: 10px 0 0px 0;
    text-align: right;
  }

  .statistics {
    display: flex;
    justify-content: space-between;
  }
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  text-align: left;
}
</style>
