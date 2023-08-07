<script setup>
import SkillScore from "@/components/SkillScore.vue";
import data from "../../data.json";

import { onMounted, ref } from "vue";

const resultsData = ref({});

onMounted(() => {
  resultsData.value = data;
});
</script>

<template>
  <Suspense>
    <main class="main">
      <div class="score-panel">
        <h1 class="score-title">Your Result</h1>
        <div class="score-circle">
          76<span class="score-limit">of 100</span>
        </div>
        <p class="score-text" id="score-text">Great</p>
        <p class="score-summary-text">
          You scored higher than 65% of the people who have taken these tests.
        </p>
      </div>
      <div class="skills-panel-wrapper">
        <span class="summary-title">Summary</span>
        <SkillScore :data="resultsData" />
        <button class="cta-btn">Continue</button>
      </div>
    </main>
  </Suspense>
</template>

<style scoped>
.main {
  max-width: 260px;
  margin: 0 auto;
  box-shadow: 0 0 1px rgba(0, 0, 0, 0.199);
}

.score-title {
  font-size: small;
  letter-spacing: 1px;
  margin-bottom: 1rem;
  color: rgba(255, 255, 255, 0.795);
  font-size: 12px;
}
.score-panel {
  background: linear-gradient(var(--slate-blue), var(--royal-blue));
  border-bottom-left-radius: 22px;
  border-bottom-right-radius: 22px;
  color: var(--default-color);
  padding: 1rem 2.5rem;
}

.score-circle {
  background: linear-gradient(var(--violet-blue) 5%, var(--persian-blue) 50%);
  display: grid;
  place-content: center;
  width: max-content;
  height: 100px;
  border-radius: 50%;
  margin: auto;
  padding: 1.5rem;
  margin-bottom: 1rem;
  font-size: 40px;
  font-family: "Hanken Grotesk Extra Bold", sans-serif;
}
.score-limit {
  display: block;
  font-size: 10px;
  letter-spacing: 1px;
  color: var(--light-lavender);
  opacity: 0.6;
}

.score-text {
  margin-bottom: 0.4rem;
  font-weight: 700;
  letter-spacing: 0.5px;
}

.score-summary-text {
  font-size: 11px;
  margin-bottom: 0.8rem;
  line-height: 15px;
  color: rgba(255, 255, 255, 0.795);
}

.skills-panel-wrapper {
  padding: 1rem 1.2rem;
}

.summary-title {
  font-weight: 800;
  font-size: 12px;
  display: block;
  text-align: left;
  margin-bottom: 1rem;
}
.cta-btn {
  all: unset;
  display: block;
  width: 100%;
  background: var(--dark-gray-blue);
  font-size: 12px;
  padding: 0.7rem 0;
  border-radius: 25px;
  color: var(--default-color);
  cursor: pointer;
  font-weight: 700;
  letter-spacing: 0.6px;
  transition: all 150ms linear;
}
.cta-btn:hover,
.cta-btn:focus {
  background: linear-gradient(var(--violet-blue), var(--persian-blue));
}
</style>
