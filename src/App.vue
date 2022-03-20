<template>
  <HelloWorld :header="header" :steps="steps" />
  <button v-on:click="markQuizz">Valider</button>
  <br />
  <br />
  <br />
  <br />
  <p>
    You can find the codesandbox for this Application with the source code here:
    <a href="https://codesandbox.io/s/vue-codesandbox-example-netlify-bz2e7j">
      https://codesandbox.io/s/vue-codesandbox-example-netlify-bz2e7j
    </a>
  </p>
</template>

<script>
import HelloWorldVue from './components/HelloWorld.vue';
export default {
  name: 'App',
  /**
   * Here is our data object that is storing the data used by the App
   * In this case the data is the steps used to make the app itself
   */
  data() {
    return {
      header: 'Quizz 1',
      // These are the steps to folow to set up the environment
      steps: [
        {
          question: 'Question ',
          multiple_answer: true,
          description: 'Intitulé de la question 1',
          answers: [
            { text: 'réponse 1.1t', right_answer: true },
            { text: 'réponse 1.2' },
            { text: 'réponse 1.3' },
            { text: 'réponse 1.4' },
          ],
        },
        {
          question: 'Question ',
          multiple_answer: true,
          description: 'Intitulé de la question 2',
          answers: [
            { text: 'réponse 2.1t', right_answer: true },
            { text: 'réponse 2.2t', right_answer: true },
            { text: 'réponse 2.3' },
            { text: 'réponse 2.4' },
          ],
        },
        {
          question: 'Question ',
          multiple_answer: false,
          description: 'Intitulé de la question 3',
          answers: [
            { text: 'réponse 3.1' },
            { text: 'réponse 3.2' },
            { text: 'réponse 3.3' },
            { text: 'réponse 3.4t', right_answer: true },
          ],
        },
      ],
    };
  },
  mounted() {
    /**
     * When our app loads we want to check if there
     * Is any saved data, and if there is we load it
     */
    if (localStorage.getItem('steps')) {
      try {
        //this.steps = JSON.parse(localStorage.getItem("steps"));
      } catch (e) {
        // If there is an error then we delete the saved data
        localStorage.removeItem('steps');
        localStorage.setItem('steps', this.steps);
        console.log('local data corrupted refreshing');
      }
    } else {
      localStorage.setItem('steps', this.steps);
    }
  },
  watch: {
    /**
     * Here we watch the steps variable.
     * Every time it changes, we update the local storage
     * This way our changes are saved
     */
    steps: {
      handler: function () {
        const parsed = JSON.stringify(this.steps);
        localStorage.setItem('steps', parsed);
      },
      // We want to watch deep into the array
      deep: true,
    },
  },
  components: {
    HelloWorld: HelloWorldVue,
  },

  methods: {
    markQuizz: function () {
      let score = 0;
      for (let i = 0; i < this.steps.length; i++) {
        console.log(this.steps[i]);
        let step = this.steps[i];
        let right_answers = 0;
        let wrong_answers = 0;
        for (let j = 0; j < step.answers.length; j++) {
          // check if the user has selected the answer and is right
          if (step.multiple_answer == true){
            if (typeof step.answers[j].selected !== 'undefined' && step.answers[j].selected === true) {
              if (step.answers[j].right_answer === true) {
                right_answers += 1;
                console.log('Bonne réponse');
              } else {
                wrong_answers += 1;
                console.log('mauvaise réponse');
              }
            }
          }
          else {
            if ( typeof (step.radio_select) !== "undefined" && step.answers[step.radio_select].right_answer == true ) {
              right_answers += 1; 
            }
          }
        }

        if (right_answers > 0 && wrong_answers === 0) {
          score += 1;
        }
      }

      alert(score + '/' + this.steps.length);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
