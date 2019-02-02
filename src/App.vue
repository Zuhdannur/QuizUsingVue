<template>
  <div id="app">
    <CardQuestion/>
  </div>
</template>

<script>

import 'bootstrap-vue/dist/bootstrap-vue.css'
import 'bootstrap/dist/css/bootstrap.css'
import CardQuestion from "./components/CardQuestion";

export default {
  name: 'app',
  components: {
      CardQuestion,
    Alerts,
    HelloWorld
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
  margin-top: 60px;
}
</style>
