<template>
  <div id="app">
    <h1>Auto-Ipsum</h1>
    <Ipsum></Ipsum>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Ipsum from './components/ipsum.vue'

export default {
  name: 'App',
  components: {
    Ipsum,
    HelloWorld
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  padding: 2rem;
}
</style>
