<script setup>
import SkillScore from "@/components/SkillScore.vue";
import dataInfo from "../../data.json";

import { ref } from "vue";

const resultsData = ref(dataInfo);
const scoreArray = ref([]);
const resultsAverage = ref(null);

for (let data of dataInfo) {
  scoreArray.value.push(data.score);
}

function scoreAverage(scoreArray) {
  let sum = scoreArray.value.reduce((acc, curr) => {
    return acc + curr;
  }, 0);

  let average = Math.floor(sum / scoreArray.value.length);
  return average;
}

resultsAverage.value = scoreAverage(scoreArray);
</script>

<template>
  <Suspense>
    <main class="main">
      <div class="score-panel">
        <h1 class="score-title">Your Result</h1>
        <div class="score-circle">
          {{ resultsAverage }}
          <span class="score-limit">of 100</span>
        </div>
        <p class="score-text">Great</p>
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
  box-shadow: 10px 10px 50px -15px hsla(224, 70%, 38%, 0.26);
}

.score-title {
  font-size: small;
  letter-spacing: 1px;
  margin-bottom: 1rem;
  color: rgba(255, 255, 255, 0.795);
  font-size: 12px;
}

.score-panel {
  background: linear-gradient(
    var(--slate-blue) 20%,
    hsla(244, 97%, 50%, 0.699) 45%,
    var(--royal-blue) 95%
  );
  border-bottom-left-radius: 22px;
  border-bottom-right-radius: 22px;
  color: var(--default-color);
  padding: 1.2rem 2.5rem 1rem;
}

.score-circle {
  background: linear-gradient(
    var(--violet-blue) 20%,
    hsla(241, 52%, 33%, 0.267),
    var(--persian-blue) 98%
  );
  display: grid;
  place-content: center;
  width: max-content;
  height: 95px;
  border-radius: 50%;
  margin: auto;
  padding: 1.5rem;
  margin-bottom: 1rem;
  font-size: 40px;
  font-family: var(--font-extra-bold);
}

.score-limit {
  display: block;
  font-size: 10px;
  letter-spacing: 1px;
  color: var(--light-lavender);
  opacity: 0.7;
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
  font-size: 13px;
  font-weight: 700;
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
  transition: all 1s linear;
}

.cta-btn:hover,
.cta-btn:focus {
  background: linear-gradient(hsl(252, 78%, 64%) 2%, var(--royal-blue) 95%);
}

@media (min-width: 1440px) {
  .main {
    display: flex;
    max-width: 450px;
    border-radius: 22px;
  }

  .score-panel,
  .skills-panel-wrapper {
    width: 50%;
  }

  .score-panel {
    border-radius: 22px;
    padding: 1.5rem 2.4rem 1rem;
    background: linear-gradient(var(--slate-blue) 20%, var(--royal-blue) 95%);
  }

  .score-title {
    margin-bottom: 1.2rem;
  }

  .score-circle {
    height: 115px;
    padding: 2.3rem;
    margin-bottom: 1.2rem;
  }

  .score-limit {
    margin-top: -2px;
  }

  .score-text {
    margin-bottom: 0.6rem;
  }

  .skills-panel-wrapper {
    padding: 1rem 1.4rem;
  }

  .cta-btn {
    padding: 0.6rem 0;
    margin-bottom: 0.6rem;
  }
}
</style>
