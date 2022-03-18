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
        },
        {
          name: "Select your template",
          description: "select create from a template, and then select Vue 3",
          image: "select-vue-3-sandbox.png",
        },
        {
          name: "Link Your Sandbox to Github",
          description:
            "Press the button that looks like the github cat logo and select a name for your repository and create it",
          note: "if the creation fails use the steps here to fix it",
          "note-link":
            "https://github.com/codesandbox/codesandbox-client/issues/5926",
          image: "create-github-repo.png",
        },
        {
          name: "Check your new Code Repo",
          description: "You will now have a new code repo like this one!",
          link: "https://github.com/blackbadgerlabs/vueexample",
        },
        {
          name: "Deploy your site!",
          description:
            "From Codesandbox use the rocket icon to deploy to netlify, and select log in with Github",
          image: "deploy-to-netlify.png",
        },
        {
          name: "Link the repo from Netlify",
          description:
            "You can then later log into Netlify and link the repo so you can deploy your updates",
          image: "link-repo-to-netlify.png",
        },
        {
          name: "Give your site a new domain name",
          description: "You can create a new domain name for your site in codesandbox",
          image: "change-site-domain-name.png"
        },
      ],
    };
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
