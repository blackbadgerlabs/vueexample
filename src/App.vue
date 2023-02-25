<template>
  <HelloWorld :header="header" :steps="steps" />
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
      header: "Steps we used to make this app",
      // These are the steps to folow to set up the environment
      steps: [
        {
          name: "Get a Github Account",
          description: "Register at Github",
          link: "https://github.com/",
          done: false,
        },
        {
          name: "Create Your Sandbox",
          description: "Register at stackblitz using your github account",
          link: "https://stackblitz.com/",
          done: false,
        },
        {
          name: "Select your template",
          description: "select create from a template, and then select Vue 3",
          done: false,
        },
        {
          name: "Link Your Sandbox to Github",
          description:
            "Select connect repository and create a new Github repository in the menu that comes up",
          image: "stackblitz-create-new-repo.png",
          done: false,
        },
        {
          name: "Check your new Code Repo",
          description: "You will now have a new code repo like this one!",
          link: "https://github.com/blackbadgerlabs/vueexample",
          done: false,
        },
        {
          name: "Link the repo from Netlify",
          description:
            "Log into Netlify and select add new site and then Import an existing project from a Git repository and choose the Git Repository you have created.",
          image: "import-existing-site.png",
          done: false,
        },
        {
          name: "Make sure the repo is linked so that the site updates",
          description:
            "You need to make sure that the repo is linked so that it redeplys every time you make a new commit to the main branch",
          image: "link-repo-to-netlify.png",
          done: false,
        },
        {
          name: "Give your site a new domain name",
          description:
            "You can create a new domain name for your site in netlify",
          image: "change-site-domain-name.png",
          done: false,
        },
      ],
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
