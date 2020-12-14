<template>
 <div id="main">
 <div>
  <b-nav class="nav"> 
    <b-nav-item disabled>Question {{ index+1 }}/{{ total }}</b-nav-item>
    <b-nav-item disabled>Correct {{ numCorrect }}/{{ total }} </b-nav-item>
    <button @click="counter++">Click Me</button>
    <p>{{ counter }}</p>
    <input type="text" name="" id="" v-model="someText">
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

data() {
return {
counter : 0, 
someText : '', 
}
},

watch : {

counter (newVal, oldVal) {
console.log(`Old val : ${oldVal}, newVal : ${newVal}`);  
},

someText: {
handler : 'updateCounter',
immediate : true, //As soon as element was created = create() lifecycle hook

},

},

methods : {
updateCounter() {
this.counter++;
}  
},
 
    
}
</script>


<style>
.nav{
border-bottom: 1px solid lightgray;   
padding: 10px 0px; 
}
</style>