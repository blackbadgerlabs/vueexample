<template>
  <div class="hello">
    <h1>{{ header }}</h1>
    <div v-for="(step, index) in steps" :key="step.name">
      <h2>Step {{ index + 1 }} {{ step.name }}</h2>
      <a :href="step.link" target="_blank">
        <p>
          {{ step.description }}
        </p>
      </a>
      <img v-if="step.image" alt="" :src="'/images/' + step.image" />
      <a v-if="step.note" href="step.note-link" target="_blank">
        <p class="note">{{ step.note }}</p>
      </a>
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
h3 {
  margin: 40px 0 0;
}
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
</style>
