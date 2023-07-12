<template>
  <div class="questions-ctr">
    <div class="progress">
      <div class="bar"></div>
      <div class="status">{{ this.step }} out of 3 questions answered</div>
    </div>
    <div class="single-question">
      <div class="question">{{ this.currentQuestion.q }}</div>
      <div
        class="answers"
        v-for="item in currentQuestion.answers"
        :key="item.id"
      >
        <div class="answer" @click="$emit('answerSelected', item)">
          {{ item.text }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["currentQuestion", "step"],
  emits: {
    answerSelected(data) {
      return data;
    },
  },
};
</script>
