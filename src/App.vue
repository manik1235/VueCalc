<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Calc/>
    <br>
    <hr>
    <br>
    <HelloWorld msg="Welcome to Your Vue.js App (I come from `src/App.vue`)"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Calc from './components/Calc.vue'

export default {
  name: 'app',
  components: {
    HelloWorld,
    Calc,
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
