<template>
  <div id="app">

    <!--Makes todos property available to TodoList component-->
    <TodoList v-bind:todos="todos"></TodoList>

  </div>
</template>

<script>
import TodoList from './components/TodoList';

export default {
  name: 'App',
  components: {
    TodoList
  },
  data() {
    return {
      todos: [
        {
          title: 'Todo A',
          project: 'Project A',
          done: false
        },
        {
          title: 'Todo B',
          project: 'Project B',
          done: true
        },
        {
          title: 'Todo C',
          project: 'Project C',
          done: false
        },        {
          title: 'Todo D',
          project: 'Project D',
          done: false
        }
      ]
    }
  }
};
</script>

<style>
</style>
