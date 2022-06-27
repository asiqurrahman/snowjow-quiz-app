<template>
  <Nav />
  <Quiz :questions="data" :results="allNotAnswered" :testresult="result"/>
  <Submit @submit="submit" :allNotAnswered="allNotAnswered"/>
</template>

<script>

import Nav from "./components/Nav.vue";
import Quiz from "./components/Quiz.vue";
import Submit from "./components/Submit.vue";
import json from "./questions.json";

export default {
  name: "App",
  components: {
    Nav,
    Quiz,
    Submit,
  },
  data() {
    return {
      data: json,
      allNotAnswered: null, // used to determine if all questions have been answered
      result: {}
    };
  },
  provide() {
    return {
      globaldata: this.data, // mainly used to prevent prop drilling and setting answers to questions from deeply nested components
    }
  },
  methods: {
    quizScore(){
      let amountCorrect = this.data.filter(question => question.result === "correct")
      let percentage = (amountCorrect.length / this.data.length) * 100 // calculates percentage correct
      let removedDecimals = Math.trunc(percentage)
      this.result = {
        amountOfQuestions: this.data.length,
        amountCorrect: amountCorrect.length,
        percentage: removedDecimals
      }
    },
    submit() {
      let checkIfAnswered = this.data.map((question) => { // loops through every question and assigns a specefic value if its not answered
        if(question.userAnswer == undefined){
          question.userAnswer = null // setting this specifically to use for yellow border when not answered
        }
      })

      let condition = this.data.every((question) => typeof question.userAnswer == "number") // checks to see if every question has been answered
      
      if(condition == false){
        this.allNotAnswered = true
      }

      if(condition == true) { // if all questions are answered then add a new property of result with value of correct or wrong
        this.allNotAnswered = false
        let obj = this.data.map((question) => {
          if(question.correctAnswer === question.userAnswer){
            question.result = "correct"
          } else {
            question.result = "wrong"
          }
        })
        this.quizScore()
        window.scroll({top: 0, behavior: "smooth"}) // scrolls to top of page to reveal score
      }
    }
  }
};
</script>

<style>
 #app{
  padding-bottom: 60px;
 }
</style>
