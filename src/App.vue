<template>
  <div id="app">
    <convert></convert>
  </div>
</template>

<script>
import Convert from './components/Convert'

export default {
  name: 'app',
  components: {
    Convert
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
