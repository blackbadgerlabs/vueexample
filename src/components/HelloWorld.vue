<template>
  <div class="hello">
    <h1>{{ header }}</h1>
    <div class=  "padding-top" v-for="(step, index) in steps" :key="step.name">

      <h2 v-if="step.multiple_answer == true">
        #{{ index + 1 }} {{ step.question }}  (plusieurs réponses)
      </h2>

      <h2 v-else>
        #{{ index + 1 }} {{ step.question }}  (une réponse)
      </h2>

      <p>{{ step.description }}</p>

     <h3 v-if="step.multiple_answer == true" v-for="(answer, answer_index) in step.answers" class="answer"> <input type="checkbox" name="case" value="reponse1" v-model="answer.selected">{{answer.text}} </h3> 
      
     <h3 v-if="step.multiple_answer == false" v-for="(answer, answer_index) in step.answers" class="answer"> <input type="radio" name="reponse" :value="answer_index" v-model="step.radio_select">{{answer.text}}  </h3>



    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    header: String,
    steps: Array,
    image: String,
  },
  methods: {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.answer{
    border: 2px solid #3d3d3d;
    color: #3d3d3d;
    font-family:'Segoe UI';
    text-align: left;
}
.padding-top{
   padding-top: 50px;
}

</style>
