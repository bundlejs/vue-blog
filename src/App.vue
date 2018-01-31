<template>
  <div id="app">
    <router-view id="page"/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
  body {
    margin: 0;
    box-sizing: border-box;
    width: 100vw;
    height: 100%;
    position: absolute;
    z-index: 1;
    overflow: hidden;
  }
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    width: 100vw;
    height: 100%;
    position: absolute;
    z-index: 10;
    overflow: hidden;
  }
  #page {
    width: 100vw;
    height: 100%;
    position: relative;
    overflow: scroll;
    -webkit-overflow-scrolling : touch;
  }
</style>
