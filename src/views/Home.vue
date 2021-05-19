<template>
  <div id="app">
    <div class="appContent">
      <AddTodos v-on:add-todo="addTodo"/>
      <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
    </div>
  </div>
</template>

<script>
import Todos from '../components/Todos';
import AddTodos from '../components/AddTodo';
import axios from 'axios';

export default {
  name: 'Home',
  components: {
    Todos,
    AddTodos
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "Todo One",
          completed:false
        },
        {
          id: 2,
          title: "Todo Two",
          completed:true
        },
        {
          id: 3,
          title: "Todo Three",
          completed: false
        }
      ]

      }
    },
    methods: {
      deleteTodo(id) {
        axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
          .then(res => this.todos = this.todos.filter(todo => todo.id !== id, res.data))
          .catch(err => console.log(err));
      },
      addTodo(newTodo) {
        const {
          title, 
          completed
        }
        = newTodo;

        axios.post('https://jsonplaceholder.typicode.com/todos', {
          title, 
          completed
        })
        .then(res => this.todos = [...this.todos, res.data])
        .catch(err => console.log(err))
      }
    },
    created() {
      axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10')
        .then(res => this.todos = res.data)
        .catch(err => console.log(err))
    }
  }
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  #app {
    font-family: 'Quicksand', sans-serif;
    color: #2c3e50;
  }

  .btn {
    display: inline-block;
    border: none;
    background-color: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }

  .btn:hover {
    background-color:  #666;
  }

</style>
