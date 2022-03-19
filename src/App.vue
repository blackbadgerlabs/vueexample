<template>
  <HelloWorld :header="header" :steps="steps" />
  <br> <br> <br> <br>
  <p>You can find the codesandbox for this Application with the source code here: <a href="https://codesandbox.io/s/vue-codesandbox-example-netlify-bz2e7j"> https://codesandbox.io/s/vue-codesandbox-example-netlify-bz2e7j </a></p>
</template>

<script>
import HelloWorldVue from "./components/HelloWorld.vue";
export default {
  name: "App",
  /**
   * Here is our data object that is storing the data used by the App
   * In this case the data is the steps used to make the app itself
   */
  data() {
    return {
      header: "Quizz 1",
      // These are the steps to folow to set up the environment
      steps: [
        {
          question: "Question ",
          description: "Intitulé de la question 1",
          answer1: "réponse 1",
          answer2: "réponse 2",
          answer3: "réponse 3",
          answer4: "réponse 4",
          multiple_answer: false,
        },
        {
          question: "Question ",
          description: "Intitulé de la question 2",
          answer1: "réponse 1",
          answer2: "réponse 2",
          answer3: "réponse 3",
          answer4: "réponse 4",
          multiple_answer: true,
        },
        {
          question: "Question ",
          description: "Intitulé de la question 1",
          answer1: "réponse 1",
          answer2: "réponse 2",
          answer3: "réponse 3",
          answer4: "réponse 4",
          multiple_answer: false,
        },
      ],
      image: "",
    };
  },
  mounted() {
    /**
     * When our app loads we want to check if there
     * Is any saved data, and if there is we load it
     */
    if (localStorage.getItem("steps")) {
      try {
        this.steps = JSON.parse(localStorage.getItem("steps"));
      } catch (e) {
        // If there is an error then we delete the saved data
        localStorage.removeItem("steps");
        localStorage.setItem("steps", this.steps);
        console.log("local data corrupted refreshing")
      }
    }
    else
    {
      localStorage.setItem("steps", this.steps);
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
        localStorage.setItem("steps", parsed);
      },
      // We want to watch deep into the array
      deep: true,
    },
  },
  components: {
    HelloWorld: HelloWorldVue,
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
