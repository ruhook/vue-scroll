<template>
  <div id="app">
    <vueScroll/>
  </div>
</template>

<script>
import vueScroll from './components/vueScroll'

export default {
  name: 'app',
  components: {
    vueScroll
  }
}
</script>

<style>
html,body {
  height: 100%;
  margin: 0;
  padding: 0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100%;
}
</style>
