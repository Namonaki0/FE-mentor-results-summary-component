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
  font-family: var(--font-default);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  min-height: 100vh;
  display: grid;
  place-content: center;
}
</style>
