<script setup>
import { defineProps } from "vue";

defineProps({
  data: Object,
});
</script>

<template>
  <div
    v-for="({ category, score, icon }, i) in data"
    :key="i"
    class="skills-wrapper"
  >
    <div class="skills">
      <div class="skills-icons-wrapper">
        <img :src="icon" :alt="i" />
      </div>
      <div class="category">
        {{ category }}
      </div>
    </div>
    <div class="skills-user-score">
      {{ score }}
      <span class="limit-span"> / 100</span>
    </div>
  </div>
</template>

<style scoped>
.skills-wrapper {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-radius: 8px;
  padding: 0.7rem;
  font-size: small;
  font-weight: 700;
  margin-bottom: 0.6rem;
}

.skills-wrapper:nth-of-type(1) {
  color: var(--light-red);
  background-color: hsla(0, 100%, 67%, 0.05);
}

.skills-wrapper:nth-of-type(2) {
  color: var(--orange-yellow);
  background-color: hsl(39, 100%, 56%, 0.05);
}

.skills-wrapper:nth-of-type(3) {
  color: var(--green-teal);
  background-color: hsl(166, 100%, 37%, 0.05);
}

.skills-wrapper:nth-of-type(4) {
  color: var(--cobalt-blue);
  background-color: hsl(234, 85%, 45%, 0.05);
  margin-bottom: 1rem;
}

.skills {
  display: flex;
  align-items: center;
  font-size: 11px;
}

.skills-icons-wrapper {
  width: 15px;
}

.skills-icons-wrapper img {
  width: 100%;
}

.category {
  margin-left: 0.5rem;
  margin-bottom: 3px;
}

.skills-user-score {
  font-size: 11px;
  margin-left: 0.5rem;
  color: black;
}

.limit-span {
  color: rgba(0, 0, 0, 0.363);
  font-size: 11px;
  margin: 3px;
}

@media (min-width: 1440px) {
  .skills-wrapper {
    padding: 0.6rem;
  }

  .skills-wrapper:nth-of-type(4) {
    margin-bottom: 1.5rem;
  }
}
</style>
