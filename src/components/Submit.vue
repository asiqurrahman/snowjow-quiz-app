<template>
  <div class="submission-container">
    <div class="btn">
      <button @click="$emit('submit')">Submit</button>
    </div>
    <div v-if="allNotAnswered" class="error-message">
      <p>
        Answer all questions before submitting. Unanswered questions are
        displayed in yellow.
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Submit",
  props: {
    allNotAnswered: Boolean,
  },
  emits: ['submit']
};
</script>

<style scoped>

.submission-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.btn button {
  all: unset;
  color: white;
  background-color: #1c790a;
  margin-top: 20px;
  padding: 10px 15px 10px 15px;
  border: 2px solid black;
  border-radius: 5px;
  cursor: pointer;
}

.error-message p {
  color: red;
  margin-top: 20px;
  margin-bottom: 30px;
}

/* Phone */
@media screen and (max-width: 500px) {
  .error-message p {
    text-align: center;
  }
}
</style>
