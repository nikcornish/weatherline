<template>
  <div id="app">
    <linetest></linetest>
  </div>
</template>

<script>
import Linetest from '@/components/Linetest.vue';
export default {
  name: 'App',
  components: {
    Linetest
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
