<template>
 <div id="main">
 <div>
  <b-nav class="nav">
    <b-nav-item disabled>Question {{index+1}}/10</b-nav-item>
    <b-nav-item disabled>Correct 0/10</b-nav-item>
  </b-nav>
</div>
 </div>   
</template>


<script>
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

export default {

data() {
return {

}
},  

 props : {
  index : Number,
 },
 
//  mounted (){
//  this.a = 1;
//  }
    
}
</script>


<style>
.nav{
border-bottom: 1px solid lightgray;   
padding: 10px 0px; 
}
</style>