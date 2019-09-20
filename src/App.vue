<template>
<div id="app">
  <div class="calculator-app">
    <Calc/>
  </div>
</div>
</template>

<script>
import Calc from './components/Calc.vue'

export default {
  name: 'app',
  components: {
    Calc
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

.calculator-app {
  border: 3px solid green;
  margin-left: auto;
  margin-right: auto;
  max-width: 300px;
  padding: 30px 30px;
  width: 50%;
}
</style>
