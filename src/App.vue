<template>
  <div id="app">
    <Messages />
    <Footer/>
  </div>
</template>

<script>
import Messages from './components/Messages'

export default {
  name: 'app',
  components: {
    Messages
  }
}
</script>

<style>

html,
body {
  background-color: #fafafa;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
