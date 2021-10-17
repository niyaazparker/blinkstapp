<template>
  <div id="app">
    <Security/>
  </div>
</template>

<script>
import Security from './components/Security.vue'

export default {
  name: 'App',
  components: {
    Security
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
