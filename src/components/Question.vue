<template>
  <div class="question-container" :class="[answered, result]">
    <div class="question">
      <p>{{ number + 1 }}. {{ question.question }}</p>
      <Choice :choices="question.choices" :id="number" />
    </div>
    <div class="result">
      <p class="correct-text" v-if="question.result == 'correct'">Correct</p>
      <p class="wrong-text" v-else-if="question.result == 'wrong'">Wrong</p>
    </div>
  </div>
</template>

<script>
import Choice from "./Choice.vue";

export default {
  name: "Question",
  props: {
    question: Object,
    number: Number,
  },
  components: {
    Choice,
  },
  computed: {
    answered() {
      if (this.question.userAnswer === null) {
        return "not-answered";
      }
    },
    result() {
      if (this.question.result === "correct") {
        return "correct";
      } else if (this.question.result === "wrong") {
        return "wrong";
      }
    },
  },
};
</script>

<style scoped>

.question-container {
  position: relative;
  width: 65vw;
  height: fit-content;
  background-color: #ffffff;
  border-radius: 7px;
  box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
  margin-top: 20px;
  padding-bottom: 25px;
}

.not-answered {
  border: 2.5px solid #dcde53;
}

.question {
  padding-left: 30px;
  padding-top: 15px;
}

.correct {
  border: 2.5px solid green;
}

.wrong {
  border: 2.5px solid red;
}

.result {
  position: absolute;
  right: 10px;
  bottom: 10px;
}

.correct-text {
  color: green;
  font-weight: bold;
}

.wrong-text {
  color: red;
  font-weight: bold;
}

@media screen and (max-width: 1024px) {
  .question-container {
    width: 85vw;
    margin-left: 20px;
  }
}

/* phone */
@media screen and (max-width: 500px) {
  .question-container {
    margin: 0px;
    margin-top: 25px;
  }

  .question p {
    max-width: 300px;
    overflow-wrap: break-word;
  }

  .question-container {
    width: 90vw;
  }

}
</style>
