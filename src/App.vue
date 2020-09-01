<template>
  <section id="app">
    <TodoHeader />
    <TodoForm label="Task name" submitText="Add task" :submitHandler="addTask" :disabled="!canAdd"/>
    <TodoList :data="tasks"/>
    <div class="statistics">
      <p id="complete"><strong>Completed:</strong> {{ getCompletedTasks() }} / {{ tasks.length }}</p>
      <p id="limit" v-bind:class="{alert: !canAdd}"><strong>Limit:</strong> {{tasks.length}} / {{ limit }}</p>
    </div>
    
  </section>
</template>

<script>
import tasks from './assets/scripts/data.js';
import TodoHeader from './components/TodoHeader';
import TodoForm from './components/TodoForm';
import TodoList from './components/TodoList';

export default {
  name: 'App',
  components: {
    TodoHeader,
    TodoList,
    TodoForm
  },
  data() {
    return {
      tasks: tasks,
      limit: 5,
    } 
  },
  computed: {
    canAdd: function () {
      return this.tasks.length < this.limit
    }
  },
  methods: {
    getCompletedTasks: function() {
      let completed = 0;
      this.tasks.forEach(task => { if (task.isDone) completed++; })

      return completed;
    },
    addTask: function(task) {
      this.tasks.push({
        id: this.tasks.length + 1,
        name: task,
        isDone: false
      })
    }
  }
}
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  text-align: left;
}

body {
  background: #e7e7e7;
}

.box {
  background: white;
  box-shadow: 0px 6px 10px 0px #c6c6c6;
  padding: 16px 32px;
}

.alert {
  color: rgb(168, 3, 3);
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

    &.alert {
      @extend .alert;
    }
  }

  .statistics {
    display: flex;
    justify-content: space-between;
    background: white;
    box-shadow: 0px 6px 10px 0px #c6c6c6;
    padding: 16px 32px;
  }
}
</style>
