<template>
  <div class="hello">
    <h1>{{ header }}</h1>
    <div v-for="(step, index) in steps" :key="step.name">
      <h2 v-if="step.multiple_answer == true">#{{ index + 1 }} {{ step.question }}  (plusieurs réponses)</h2>
      <h2 v-else>#{{ index + 1 }} {{ step.question }}  (une réponse)</h2>

        <p>{{ step.description }}</p>
        
       <h3 v-if="step.multiple_answer == true" class="answer"> <input type="checkbox" id="check_box1" name="case" value="reponse1">{{step.answer1}} </h3> 
       <h3 v-if="step.multiple_answer == true" class="answer"> <input type="checkbox" id="check_box2" name="case" value="reponse2">{{step.answer2}} </h3> 
       <h3 v-if="step.multiple_answer == true" class="answer"> <input type="checkbox" id="check_box3" name="case" value="reponse3">{{step.answer3}} </h3> 
       <h3 v-if="step.multiple_answer == true" class="answer"> <input type="checkbox" id="check_box4" name="case" value="reponse4">{{step.answer4}} </h3> 


       <h3 v-if="step.multiple_answer == false" class="answer"> <input type="radio" id="radio1" name="reponse" >{{step.answer1}} </h3> 
       <h3 v-if="step.multiple_answer == false" class="answer"> <input type="radio" id="radio2" name="reponse" >{{step.answer2}} </h3> 
       <h3 v-if="step.multiple_answer == false" class="answer"> <input type="radio" id="radio3" name="reponse" >{{step.answer3}} </h3> 
       <h3 v-if="step.multiple_answer == false" class="answer"> <input type="radio" id="radio4" name="reponse" >{{step.answer4}} </h3> 
       
      <br><br><br><br><br>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    header: String,
    steps: Array,
  },
  methods: {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #000000;
}

.note {
  color: #42b983;
}

.answer{
    border: 2px solid #3d3d3d;
    
}

</style>
