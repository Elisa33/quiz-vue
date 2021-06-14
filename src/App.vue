<template>
  <div id="app">
    <h1>Vue Quiz</h1>
    <QuizTest/>
  </div>
</template>

<script>

import QuizTest from './components/QuizTest.vue'

export default {
  name: 'App',
  components: {
    QuizTest
  }
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #5a5a5a;
  margin-top: 30px;
}
body{
  background: #efefef;
}
</style>
