<template>
  <div id="app">
    <AppHeader/>

    <AppMain/>

    <AppFooter/>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import AppMain from './components/AppMain.vue'
import AppFooter from './components/AppFooter.vue'

export default {
  name: 'App',
  components: {
    AppHeader,
    AppMain,
    AppFooter,
  }
}
</script>

<style lang="scss">
// google fonts import
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');
// GENERAL RULES
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
  
#app {
  font-family: 'Roboto', Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
