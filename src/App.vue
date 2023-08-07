<template>
  <ResultsComponent />
</template>

<script>
import ResultsComponent from "./components/ResultsComponent.vue";

export default {
  name: "App",
  components: {
    ResultsComponent,
  },
};
</script>

<style>
#app {
  font-family: "Hanken Grotesk Default", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  min-height: 100vh;
  display: grid;
}
</style>
