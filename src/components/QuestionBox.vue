<template>
<div id="main" class="mt-5">


    <div>
    <b-jumbotron>
        <!-- Question -->
        <h1>{{currentQuestion.question}}</h1>

        <!-- Answers -->
        <b-list-group class="mb-3">
        <b-list-group-item :key="answer" v-for="answer in createArr">{{answer}}</b-list-group-item>
        </b-list-group>

        <b-button variant="success btn-lg mr-2">Submit</b-button>
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


// methods () {
// createArr () {
// let answers = [...this.currentQuestion.incorrect_answers],
// return answers,   
// }  
// },


}

</script>

<style>

</style>