<template>
  <div id="app">
  <Header />

  <b-container class="bv-example-row">
  <b-row>
    <b-col sm="6" offset="3"><QuestionBox /></b-col>
  </b-row>
 </b-container>

  </div>
</template>

<script>
// Importing Components to Parent File (App)
import Header from './components/Header.vue'
import QuestionBox from './components/QuestionBox.vue'

export default {
  name: 'App',
  components: {
  Header,
  QuestionBox 
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
}
</style>
