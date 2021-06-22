<template>
  <div>
    <div class="question">{{ question }}</div>

    <div :key="answer" v-for="answer in answers">
      <div class="answer hover" :value="answer" @click="answered">
        {{ answer }}
      </div>
    </div>

    <div class="info">
      <span class="datum">{{ category }}</span>
      <span class="datum">Type: {{ type }}</span>
      <span class="datum">Difficulty: {{ difficulty }}</span>
    </div>
  </div>
</template>
<script>
import { shuffle } from "../utils/shuffle";

export default {
  name: "QuizQuestion",
  props: [
    "id",
    "question",
    "category",
    "type",
    "difficulty",
    "correctAnswer",
    "incorrectAnswers",
  ],
  data() {
    return {
      answers: [],
    };
  },
  created() {
    this.answers = shuffle([...this.incorrectAnswers, this.correctAnswer]);
  },
  methods: {
    unescape(string) {
      this.icon = document.querySelector(".check");
      this.icon.innerHTML = string;
    },
    answered(event) {
      this.selected = event.target.attributes.value.value;
      const correct = (this.selected === this.correctAnswer);

      this.$emit('answered', correct);
    },
  },
};
</script>
<style>
</style>