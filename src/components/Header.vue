<template>
 <div id="main">
 <div>
  <b-nav class="nav"> 
    <b-nav-item disabled>Question {{ index+1 }}/{{ total }}</b-nav-item>
    <b-nav-item disabled>Correct {{ numCorrect }}/{{ total }} </b-nav-item>
  </b-nav>
</div>
 </div>   
</template>


<script>
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

export default {

 props : {
  index : Number,
  total : Number,
  numCorrect : Number,
 },
 
    
}
</script>


<style>
.nav{
border-bottom: 1px solid lightgray;   
padding: 10px 0px; 
}
</style>