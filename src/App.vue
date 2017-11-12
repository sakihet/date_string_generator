<template>
  <div id="app">
    <DateStringGenerator/>
  </div>
</template>

<script>
import DateStringGenerator from './components/DateStringGenerator'

export default {
  name: 'app',
  components: {
    DateStringGenerator
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
}
</style>
