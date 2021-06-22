<template lang="">
  <div class="container">
    <div class="title">
      <h2>Question {{ index + 1 }}/10</h2>
    </div>

    <Question
      :key="items[index].id"
      :id="item.id"
      :question="item.question"
      :category="item.category"
      :type="item.type"
      :difficulty="item.difficulty"
      :correctAnswer="item.correct_answer"
      :incorrectAnswers="item.incorrect_answers"
      @answered="answered"
    ></Question>

    <!-- popup -->
    <div class="popup" v-show="showPopup">
      <div class="check" v-html="icon" :class="popupClass" v-show="index < 9">
      </div>
      <button class="next" @click="next" v-show="index < 9">Next</button>
    </div>

    <div class="finish" v-show="index == 9">
      <span>Correct Answers:</span>
      <span>{{ correctAnswers }}/10</span>
      <button class="reset" @click="reset">Reset</button>
    </div>
  </div>
</template>

<script>
import { shuffle } from "../utils/shuffle";
import Question from "./QuizQuestion.vue";

export default {
  name: "QuizQuestions",
  props: ["data"],
  components: { Question },
  data() {
    return {
      index: 0,
      selected: "",
      correctAnswers: 0,
      showPopup: false,
      popupClass: null,
      icon: "",
      items: shuffle(this.data),
    };
  },
  computed: {
    item() {
      return this.items[this.index];
    },
  },
  methods: {
    unescape(string) {
      this.icon = document.querySelector(".check");
      this.icon.innerHTML = string;
    },
    answered(selected) {
      this.showPopup = true;

      if (selected) {
        this.correctAnswers++;
        this.popupClass = "correct";
        this.icon = "&check;";
      } else {
        this.popupClass = "incorrect";
        this.icon = "&#x2E3;";
      }
    },
    popreset() {
      this.showPopup = false;
    },
    next() {
      this.index++;
      this.popreset();
    },
    reset() {
      this.index = 0;
      this.correctAnswers = 0;
    },
  },
};
</script>

<style lang=""></style>
