<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <PlayControllers></PlayControllers>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import PlayControllers from './components/PlayControllers.vue'
export default {
  name: 'App',
  components: {
    // HelloWorld,
    PlayControllers,
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
