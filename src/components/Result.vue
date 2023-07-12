<template>
  <div class="result">
    <div class="title">{{ this.resultScore.title }}</div>
    <div class="desc">{{ this.resultScore.desc }}</div>
  </div>
</template>
<script>
export default {
  props: ["resultScore"],
};
</script>
