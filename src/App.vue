<template>
  <div id="app">
    <UserComp />
  </div>
</template>

<script>
import UserComp from './components/User.vue'

export default {
  name: 'App',
  components: {
    UserComp
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
