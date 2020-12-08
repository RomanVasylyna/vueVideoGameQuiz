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
        @click="selectedItem"
        :key="answer" 
        v-for="(answer, ind) in shuffleArr(createArr())">
        {{answer +  ind}}
        </b-list-group-item>
        </b-list-group>

        <b-button variant="success btn-lg mr-2" @click="createArr">Submit</b-button>
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
selectedIntex : 0,
}    
},

methods : {

createArr () {
let answers = [...this.currentQuestion.incorrect_answers];
answers.push(this.currentQuestion.correct_answer);
return answers;  
}, 

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

selectedItem() {
console.log(this);
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