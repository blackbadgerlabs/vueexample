<template>
  <HelloWorld :header="header" :steps="steps" />
</template>

<script>
import HelloWorldVue from "./components/HelloWorld.vue";
export default {
  name: "App",
  data() {
    return {
      header: "How we made this app",
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
          description: "Register at codesandbox using your github account",
          link: "https://codesandbox.io/",
          done: false,
        },
        {
          name: "Select your template",
          description: "select create from a template, and then select Vue 3",
          image: "select-vue-3-sandbox.png",
          done: false,
          note:
            "Don't worry if you see this error. It's a known issue with Codesandbox",
          note_image: "sandbox-error-message.png",
          note_link:
            "https://github.com/codesandbox/codesandbox-client/issues/6194",
        },
        {
          name: "Link Your Sandbox to Github",
          description:
            "Press the button that looks like the github cat logo and select a name for your repository and create it",
          note: "if the creation fails use the steps here to fix it",
          note_link:
            "https://github.com/codesandbox/codesandbox-client/issues/5926",
          image: "create-github-repo.png",
          done: false,
        },
        {
          name: "Check your new Code Repo",
          description: "You will now have a new code repo like this one!",
          link: "https://github.com/blackbadgerlabs/vueexample",
          done: false,
        },
        {
          name: "Deploy your site!",
          description:
            "From Codesandbox use the rocket icon to deploy to netlify, and select log in with Github",
          image: "deploy-to-netlify.png",
          done: false,
        },
        {
          name: "Link the repo from Netlify",
          description:
            "You can then later log into Netlify and link the repo so you can deploy your updates",
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
      }
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
      // We want to run the watcher as soon as the app loads
      immediate: true,
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
