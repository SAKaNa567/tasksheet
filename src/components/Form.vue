<template >
  <div class="form">
    <h2 style="text-align:center;">Todo</h2>
<div id="todo-list-example">
    <form v-on:submit.prevent="addNewTodo">
      <label for="new-todo"></label>
      <input
        v-model ="newTodoText"
        id="new-todo"
        placeholder="input your task">
    </form>
<ul>
      <li
      is="TodoItem"
      v-for="(todo,index) in todos"
      v-bind:key="todo.id"
      v-bind:title="todo.title"
      v-on:remove="todos.splice(index,1)"
      ></li>
</ul>
</div>


  </div>
</template>
<script>
import TodoItem from './TodoItem.vue'

export default {
  data: function(){
    return {
      newTodoText: '',
      todos:[],
      nextTodoId: 0

    }
  },
  methods: {
    addNewTodo: function () {
      this.todos.push({
        id: this.nextTodoId++,
        title: this.newTodoText
      })
      this.newTodoText = ''
    }
  },
  components: {
    TodoItem,
  }
}

</script>
<style media="screen">
  .form{
    /* border: solid  10px black; */
    margin: 10px;
    width: 30%;
    height: 500px;
    background-color: #f09199;

  }
  #todo-list-example {
    text-align: center;
  }

</style>
