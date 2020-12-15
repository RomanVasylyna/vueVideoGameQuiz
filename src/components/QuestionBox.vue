<template>
<div id="main" class="mt-5">

    <div>
    <b-jumbotron>
        <!-- Question -->
        <h1>{{ currentQuestion.question }}</h1>

        <!-- Answers -->
        <b-list-group class="mb-3">
        <b-list-group-item 
        class="list-item"
        @click="selectedItem(ind)"
        :class="showAnswers(ind)"
        :key="answer" 
        v-for="(answer, ind) in answers">
        {{ answer }}
        </b-list-group-item>
        </b-list-group>

 <!-- If user has not selected anything or if he already answered block the btn -->
        <b-button variant="success btn-lg mr-2" 
        :disabled="selectedIndex === null || answered"
        @click="submitAnswer">
        Submit
        </b-button>

        <b-button variant="primary btn-lg" 
        @click="next">
        Next
        </b-button>

    </b-jumbotron>
    </div> 
    

   
</div>    
</template>

<script>
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

export default {
 
props : {
currentQuestion : Object,
next : Function,
correctAnswers : Function,
}, 


data() {
return {
selectedIndex : null, //Currently Selected Answer Index
mixedArr : [],        //Mixed array of answers
correctIndex : null,  //Correct question's index
answered : false,     //Meaning question wasn't answered
}    
},

// Watch for specific item being changed
watch : {
currentQuestion : { //This is the item we want to track
immediate : true, //As soon as it loads = create() lifecycle hook
handler() {   
this.selectedIndex = null;
this.answered = false;    
}    
}
},

computed : {

answers() {
let answers = [...this.currentQuestion.incorrect_answers]; //Copying the array
answers.push(this.currentQuestion.correct_answer);
return this.shuffleArr(answers);
}

},


methods : {

// Mix Answers Array
shuffleArr(a) {
    var j, x, i;
    for (i = a.length - 1; i > 0; i--) {
        j = Math.floor(Math.random() * (i + 1));
        x = a[i];
        a[i] = a[j];
        a[j] = x;
    }
    return a;
},

selectedItem(index) { 
this.selectedIndex = index; 
console.log(index);   
},

// Submit btn event
submitAnswer() { 
this.correctIndex = this.answers.indexOf(this.currentQuestion.correct_answer);    
let isCorrect = false; //False Boolean    

if(this.selectedIndex === this.correctIndex) { //If selected index = correct answer index (if user has chosen the correct answer)
isCorrect = true; //Boolean = true
}

this.answered = true; 
this.correctAnswers(isCorrect); // Increment number of correct answers
},

// Show correct/incorrect answers
showAnswers(ind) {
  return !this.answered && this.selectedIndex === ind ? 'selectedItem' : 
  this.answered && this.correctIndex === ind ? 'correctAnswer' :
  this.answered && this.selectedIndex === ind && this.correctIndex !== ind ? 'incorrectAnswer' : ''
},

},




}

</script>

<style>
.list-item:hover{
background:lightgray;
cursor: pointer;
}

.selectedItem{
background: lightblue;
color: #fff;    
}

.correctAnswer{
background: green;
color: #fff;    
}

.incorrectAnswer{
background: red;  
color: #fff;  
}


</style>