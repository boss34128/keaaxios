<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/itune.png" width="300px">
    <anime />
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import Anime from './components/Anime.vue'

export default {
  name: 'App',
  components: {
    //HelloWorld,
    Anime
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
  margin: 20px;
}
</style>
