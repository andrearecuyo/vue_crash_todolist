<template>
    <div class="addContent">
        <div class="addTodo">
            <h2>Add Task</h2>
            <form @submit="addTodo">
                <input v-model="title" type="text" name="title" id="" placeholder="Add Todo..." required class="input-add">
                <input type="submit" value="Submit" class="btn">
            </form>
        </div>
    </div>
</template>

<script>

export default {
    name: "AddTodo",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();
            const newTodo = {
                title: this.title,
                completed: false
            }
            //Send up to parent.
            this.$emit('add-todo', newTodo) ;    
            
            this.title = '';
        }
    }
}
</script>

<style scoped>

    .addContent {
        display: flex;
        justify-content: center;
        margin-bottom: 20px;
    }
    .addTodo {
        width: 800px;
    }

    .addTodo h2 {
        text-align: left;
        margin-top: 20px;
        margin-bottom: 10px;
    }
    form {
        display: flex;
        justify-content: center;
    }

    input [type="text"] {
        flex: 10;
    }

    input [type="submit"] {
        flex: 2;
    }

    .input-add {
        width: 100%;
        font-family: 'Quicksand', sans-serif;
        padding: 12px 20px;
        border: 1px #e7e7e7 solid;
        -webkit-box-shadow:0 1px 4px rgba(0, 0, 0, 0.3), 0 0 40px rgba(0, 0, 0, 0.1) inset;
        -moz-box-shadow:0 1px 4px rgba(0, 0, 0, 0.3), 0 0 40px rgba(0, 0, 0, 0.1) inset;
                box-shadow:0 1px 4px rgba(0, 0, 0, 0.3), 0 0 40px rgba(0, 0, 0, 0.1) inset;
    }

    .btn {
        background-color: #2c3e50;
        border: 1px solid #2c3e50;
        font-family: 'Quicksand', sans-serif;
        
    }

    .btn:hover {
        background-color: transparent;
        color: #2c3e50;
        border: 1px solid #2c3e50;
    }
</style>