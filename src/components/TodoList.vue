<template>
  <div>
    <p>Completed Tasks: {{completedTasks()}}</p>
    <p>Pending Tasks: {{pendingTasks()}}</p>

    <todo v-on:delete-todo="deleteTodo" v-for="todo in todos" v-bind:todo="todo"></todo>
  </div>
</template>

<script type = "text/javascript" >

  import Todo from './Todo';

  export default {
    // Allows component to access todos property from main App component
    props: ['todos'],
    components: {
      Todo
    },
    methods: {
      completedTasks: function() {
        return this.todos.filter(function(todo) { return todo.done === true }).length;
      },
      pendingTasks: function() {
        return this.todos.filter(function(todo) { return todo.done === false }).length;
      },
      deleteTodo: function(item) {
        const todoIndex = this.todos.indexOf(item);
        this.todos.splice(item, 1);
      }
    }
  };
</script>
<style>
</style>
