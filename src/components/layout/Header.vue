<template>
    <header class="header">
        <h1>
            Simple TodoList
        </h1>
        <div id="nav">
            <router-link to="/">Home</router-link> |
            <router-link to="/about">About</router-link>
        </div>
    </header>
</template>

<script>
export default {
    name: "Header"
}
</script>

<style>
    .header {
        background-color: #f7f7f7;
        color: #2c3e50;
        text-align: center;
        padding-top: 20px;
    }
    
    .header a {
        color: #fff;
        padding-right: 5px;
    }
</style>