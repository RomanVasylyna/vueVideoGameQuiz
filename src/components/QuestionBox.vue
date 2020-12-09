<template>
<div id="main" class="mt-5">

    <div>
    <b-jumbotron>
        <!-- Question -->
        <h1>{{currentQuestion.question}}</h1>

        <!-- Answers -->
        <b-list-group class="mb-3">
        <b-list-group-item 
        class="list-item"
        :class="[]"
        @click="selectedItem(ind)"
        :key="answer" 
        v-for="(answer, ind) in shuffleArr()">
        {{ answer }}
        </b-list-group-item>
        </b-list-group>

        <b-button variant="success btn-lg mr-2" @click="submitAnswer">Submit</b-button>
        <b-button variant="primary btn-lg" @click="increment">Next</b-button>

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
increment : Function,
}, 

data() {
return {
selectedIndex : null,
mixedArr : [],
correctIndex : null,
}    
},

methods : {

// Mix Answers Array
shuffleArr() {
let a = [...this.currentQuestion.incorrect_answers, this.currentQuestion.correct_answer];
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
// let joinedArr = [...this.currentQuestion.incorrect_answers, this.currentQuestion.correct_answer]; 
// if(index === joinedArr.indexOf(this.currentQuestion.correct_answer)) {
console.log(this.selectedIndex);
// }  
},

submitAnswer() {
this.correctIndex = this.currentQuestion.correct_answer;
console.log(this.correctIndex);
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


</style>