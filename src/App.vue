<template>
  <div id="app">
    <component :is="which"></component>
  </div>
</template>

<script>

import Answer from './components/Answer';
import Question from './components/Question'
export default {
  name: 'App',
  data(){
    return{
      which : 'app-Question'
    }
  },
  components: {
    appQuestion : Question,
    appAnswer : Answer
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
