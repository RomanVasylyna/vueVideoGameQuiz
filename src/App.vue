<template>
  <div id="app">
  <Header 
  :index="index"
  :total="numTotal"
  :numCorrect="numCorrect"
  
  />

  <b-container class="bv-example-row">
  <b-row>
    <b-col sm="6" offset="3">
    <QuestionBox 
    v-if="questions.length"
    :currentQuestion="questions[index]"
    :next="next"
    :correctAnswers="correctAnswers"
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
  questions : [], //Put API response into array
  index : 0, 
  numCorrect : 0, //Increase Number of Correct Answers
  numTotal : 0,  //Total Number of Answers
  }    
  }, 

  methods : {
  
  // Increment Amount of Question Passed
  next() {
  while(this.index < 9) {
  this.index++;
  console.log(this.index);
  break;
  }  
  },

  correctAnswers(isCorrect) {
  if(isCorrect) {
  while(this.numCorrect < 10) {
  this.numCorrect++;  
  break;
  } 
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
  this.numTotal = this.questions.length;
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
