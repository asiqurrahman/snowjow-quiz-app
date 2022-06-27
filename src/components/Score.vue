<template>
    <div class="score-container">
        <p class="title">Results</p>
        <p class="ratio">You got {{testresult.amountCorrect}} / {{testresult.amountOfQuestions}} questions correct</p>
        <p class="percentage">{{testresult.percentage}} %</p>
    </div>
</template>
<script>
export default {
  name: "Score",
  props: {
    testresult: Object
  },
};
</script>

<style scoped>
.score-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  color: #454D55;
  font-size: 1.1em;
}

.title {
  text-decoration: underline 1.5px;
}

.ratio {
  margin-top: 15px;
  margin-bottom: 5px;
}

.percentage {
  color: red;
  font-weight: bolder;
}
</style>
