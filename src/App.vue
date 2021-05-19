<template>
  <div id="app">
    <Header />
    <router-view/>
  </div>
</template>

<script>
import Header from './components/layout/Header';

export default {
  name:"app",
  components: {
    Header
  }
}
</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Quicksand:wght@300;400&display=swap');

#app {
  font-family: 'Quicksand', sans-serif;
  text-align: left;
  color: #2c3e50;
  background: #f7f7f7;
  max-height: 100%;
  padding-bottom: 30px;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

@media (max-width: 600px) {
  #app {
    padding: 20px;
  }
}
</style>
