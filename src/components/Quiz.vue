<template>
  <div class="container">
    <div class="content">
      <div class="header">
        <h1>Quiz 1 - HTML / CSS / JS Practice</h1>
      </div>
      <div v-show="results === false">
        <Score :testresult="testresult"/>
      </div>
      <div v-for="(question, index) in questions" v-bind:key="question">
        <Question :question="question" :number="index" />
      </div>
    </div>
  </div>
</template>

<script>
import Question from "./Question.vue";
import Score from "./Score.vue";

export default {
  name: "Quiz",
  props: {
    questions: Array,
    results: Boolean,
    testresult: Object,
  },
  components: {
    Question,
    Score,
  },
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  padding-top: 50px;
}


.header {
  margin: 10px 0px 10px 0px;
}

.header h1 {
  color: #454d55;
}

/* tablet */
 @media screen and (max-width: 1024px) {
  .container {
    justify-content: flex-start;
  }

  .header {
    margin-left: 50px;
    font-size: .8em;
  }
 }

/* phone */
@media screen and (max-width: 500px) {
  .container {
    justify-content: center;
  }

  .header {
    margin-left: 20px;
  }

  .content {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
}
</style>
