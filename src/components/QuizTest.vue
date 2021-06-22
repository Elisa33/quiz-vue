<template>
  <div>
    <QuizQuestions :data="data" />
  </div>
</template>

<script>
import QuizQuestions from "./QuizQuestions.vue";
import data from "../data.json";

export default {
  components: { QuizQuestions },
  data() {
    return {
      data,
    };
  },
};
</script>

<style></style>
