<template>
  <div id="app">
  <Header />

  <b-container class="bv-example-row">
  <b-row>
    <b-col sm="6" offset="3"><QuestionBox 
    :currentQuestion="questions[index]"
    
    :increment="increment"
    /></b-col>
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
  },

  data () {
  return {
  questions : [],
  index : 0, 
  }    
  }, 

  methods : {

  increment() {
  while(this.index < 10) {
  this.index++;
  console.log(this.index);
  break;
  }  
  },

  },

  // Function That Fires Off as soon as elem is created
  mounted : function() {   
  fetch('https://opentdb.com/api.php?amount=10&category=15&type=multiple'
  )
  .then(res => res.json())
  .then(resJson => {
  this.questions = resJson.results;
  console.log(this.questions);
  })
  .catch(err => console.log(err));
  },  


}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
}
</style>
