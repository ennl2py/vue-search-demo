<template>
  <div id="app">
    <com-search></com-search>
  </div>
</template>

<script>
import ComSearch from "./components/search"

export default {
  name: 'App',
  components: {
    ComSearch
  }
}
</script>

<style>
html body {
  margin: 0;
  padding: 0
}

body {
  background: url('./assets/bg.jpg') no-repeat fixed;
  background-position: center
}

#app {
  text-align: center;
}
</style>
