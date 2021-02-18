<template>
<div>
<Header />
<AddTodo v-on:send-parent-todo="addNewTodo" />
<Todos v-bind:myTodos="todos" v-on:del-todo="deleteTodo"  />
</div>
</template>

<script>
import  Header from './components/layout/Header';
import AddTodo from './components/AddTodo';
import Todos from './components/Todos';

export default {
  name: "App",
  components: {
   Header,
   AddTodo,
   Todos,

  },
  data(){
    return {
      todos: []
    }
  },
  methods: {
    deleteTodo (id){
      fetch(`https://jsonplaceholder.typicode.com/todos/${id}`,{
          method: 'DELETE', 
        })
         .then(response=>response.json())
        .then(()=> {
          this.todos = this.todos.filter(todo=> todo.id !== id);
        })
        .catch((error)=>{
          console.error('Error:',error);
        })
        
    },
    addNewTodo (newTodo) {
       const { title, completed } = newTodo;
       fetch('https://jsonplaceholder.typicode.com/todos',{
          method: 'POST', 
          headers: {
            'Content-Type': 'application/json',
          },
          body: JSON.stringify({
            title,
            completed
          }),
        })
        .then(response=>response.json())
        .then(data=> {
          this.todos = [...this.todos, data]
        })
        .catch((error)=>{
          console.error('Error:',error);
        })
       
       
   
    }
  },
  created () {

     fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
     .then((response)=> response.json())
     .then((data)=>{

          this.todos = [...data];
          console.log(this.todos);
     })
      .catch((error)=>{
          console.error('Error:',error);
        })
       
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
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover {
  background: #666;
}
</style>
