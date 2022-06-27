<template>
  <div class="choice">
    <div v-for="(choice, index) in choices" v-bind:key="index">
      <label :class="[index == correctAnswer ? 'correct-answer' : '']">
        <input type="radio" :name="`answer-${id}`" @click="answer(globaldata, id, index)"/>
        <span class="label-text">{{ choice }}</span>
      </label>
    </div>
  </div>
</template>

<script>
export default {
  name: "Choice",
  inject: ['globaldata'],
  props: {
    choices: Array,
    id: Number
  },
  methods: {
    answer(globaldata, question_id, answer_id,) { //setting the users answer to this question by adding a new property
      let obj = globaldata[question_id]
      obj.userAnswer = answer_id
    }
  },
  computed: {
    correctAnswer() {
      let obj = this.globaldata[this.id]
      if(obj.result == "wrong"){
        return obj.correctAnswer
      }
    }
  }
  
};
</script>

<style scoped>
label {
    display: flex;
    align-items: center;
    margin: 15px 0px 0px 25px;
    width: 44vw;
}

input {
  cursor: pointer;
}

.label-text {
    margin-left: 10px
}

.correct-answer {
  color: white;
  background-color: #24A824;
  padding: 10px;
  border: 2px solid black;
  border-radius: 10px;
  margin-left: 15px;
}

/* tablet */
 @media screen and (max-width: 1024px) {
  label {
    margin-left: 0px;
  }

  .correct-answer {
    margin-left: -12px;
  }
 }
 
/* phone */
@media screen and (max-width: 500px) {
  label {
    width: 70vw;
  }
}
</style>