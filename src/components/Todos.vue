<template>
    <div class="app">
        <div class="contentTodos">
            <div v-bind:key="todo.id" v-for="todo in todos">
                <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" />
            </div>
        </div>
    </div>
</template>

<script>
import TodoItem from './TodoItem.vue';

export default {
    name: "Todos",
    components: {
        TodoItem
    },
    props: ["todos"]
}
</script> 

<style>

  .contentTodos {
    position: relative;
    width: 800px;
    height: 100%;
    border: 1px #e7e7e7 solid;
    -webkit-box-shadow:0 1px 4px rgba(119, 119, 119, 0.3), 0 0 40px rgba(0, 0, 0, 0.1) inset;
       -moz-box-shadow:0 1px 4px rgba(0, 0, 0, 0.3), 0 0 40px rgba(0, 0, 0, 0.1) inset;
            box-shadow:0 1px 4px rgba(0, 0, 0, 0.3), 0 0 40px rgba(0, 0, 0, 0.1) inset;
  }

  .app {
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>