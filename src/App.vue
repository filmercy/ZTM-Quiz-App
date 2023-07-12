<template>
  <div class="ctr">
    <Questions
      v-if="questionsAnswered < questions.length"
      :currentQuestion="questions[questionsAnswered]"
      :step="questionsAnswered + 1"
      @answerSelected="updateScore"
    />
    <Result :resultScore="checkResult" v-else />
    <button type="button" class="reset-btn" @click="resetScore">Reset</button>
  </div>
</template>

<script>
import Questions from "./components/Questions.vue";
import Result from "./components/Result.vue";
import MyComponent from "./components/MyComponent.vue";

export default {
  name: "App",
  components: {
    Questions,
    Result,
    MyComponent,
  },
  data() {
    return {
      score: 0,
      questionsAnswered: 0,
      questions: [
        {
          q: "What is 2 + 2?",
          answers: [
            {
              text: "4",
              is_correct: true,
            },
            {
              text: "3",
              is_correct: false,
            },
            {
              text: "Fish",
              is_correct: false,
            },
            {
              text: "5",
              is_correct: false,
            },
          ],
        },
        {
          q: 'How many letters are in the word "Banana"?',
          answers: [
            {
              text: "5",
              is_correct: false,
            },
            {
              text: "7",
              is_correct: false,
            },
            {
              text: "6",
              is_correct: true,
            },
            {
              text: "12",
              is_correct: false,
            },
          ],
        },
        {
          q: "Find the missing letter: C_ke",
          answers: [
            {
              text: "e",
              is_correct: false,
            },
            {
              text: "a",
              is_correct: true,
            },
            {
              text: "i",
              is_correct: false,
            },
          ],
        },
      ],
      results: [
        {
          min: 0,
          max: 2,
          title: "Try again!",
          desc: "Do a little more studying and you may succeed!",
        },
        {
          min: 3,
          max: 3,
          title: "Wow, you're a genius!",
          desc: "Studying has definitely paid off for you!",
        },
      ],
    };
  },
  methods: {
    updateScore(data) {
      this.questionsAnswered++;
      data.is_correct ? this.score++ : this.score;
    },
    resetScore() {
      this.questionsAnswered = 0;
      this.score = 0;
    },
  },
  computed: {
    checkResult() {
      return this.score < 3 ? this.results[0] : this.results[1];
    },
  },
};
</script>
