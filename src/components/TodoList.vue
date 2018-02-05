<template>
  <div>
    <p>Completed Tasks: {{completedTasks()}}</p>
    <p>Pending Tasks: {{pendingTasks()}}</p>

    <Todo v-on:complete-todo="completeTodo" v-on:delete-todo="deleteTodo" v-for="todo in todos" v-bind:todo="todo"></Todo>
    <CreateTodo v-on:create-todo="createTodo"></CreateTodo>
  </div>
</template>

<script type = "text/javascript" >

  import Todo from './Todo';
  import CreateTodo from './CreateTodo';

  export default {
    // Allows component to access todos property from main App component
    props: ['todos'],
    components: {
      Todo,
      CreateTodo
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
        this.todos.splice(todoIndex, 1);
      },
      createTodo: function(newItem) {
        this.todos.push(newItem);
      },
      completeTodo: function(item) {
        const todoIndex = this.todos.indexOf(item);
        this.todos[todoIndex].done = !item.done;
      }

    }
  };
</script>
<style>
</style>
