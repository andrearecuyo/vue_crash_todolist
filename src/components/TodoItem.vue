<template>
    <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
        <p>
            <input type="checkbox" v-on:change="markComplete">
            {{todo.title}}
            <button @click="$emit('del-todo', todo.id)" class="del">Delete</button>
        </p>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo"],
    methods: {
        markComplete() {
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>

<style>

    
    .todo-item {

        background-color: #f7f7f7;
        padding:20px;
        border-bottom: 1px #e7e7e7 solid;
    }

    .is-complete {
        text-decoration: line-through;
        color: #ff6e6e;
    }

    .del {

        background-color: #ff6e6e;
        color:#fff;
        border: 1px #ff6e6e solid;
        padding: 5px 10px;
        cursor: pointer;
        float:right;
        font-family: 'Quicksand', sans-serif;
    }

    .del:hover{

        background-color: transparent;
        border: 1px #ff6e6e solid;
        color: #2c3e50;
    }

</style>