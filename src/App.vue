<template>

  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Header from './components/layout/Header';
import Todos from './components/Todos';
import AddTodo from './components/AddTodo';

export default {
  name: 'app',
  components: {
    Header,
    Todos,
    AddTodo
  },
  data(){
    return {
      todos: [
       {
          completed:false,
          id:"1",
          title:"Napisati diplomski rad"
       },
        {
          completed:false,
          id:"2",
          title:"Ispraviti diplomski rad"
       },
       {
          completed:false,
          id:"3",
          title:"Obraniti diplomski rad"
       }
      ]
    }
  },
  methods: {
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id != id);
    },
    addTodo(newTodo){
      this.todos = [...this.todos, newTodo];
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
.btn {
  display: inline-block;
  border: none;
  background: rgb(19, 18, 31);
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover {
  background: rgb(0, 0, 0);
}
</style>
