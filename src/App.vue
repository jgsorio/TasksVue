<template>
  <div id="app">
    <header>
      Minhas Tarefas
    </header>
    <TaskList />
  </div>
</template>

<script>
import TaskList from './components/Task';

export default {
  name: 'App',
  components: {
    TaskList
  }
}
</script>

<style scoped>
  header {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 80px;
    font-size: 40px;
    color: #FFF;
  }
</style>