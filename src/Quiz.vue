<template>
  <div id="body">
    <!--<pre>{{ JSON.stringify(questions, ["text"], 2) }}</pre>-->
    <div id="questions" v-if="quizStage" v-bind:key="question.id" v-for="question in questions">
      <Question
        v-bind:question="question"
        v-bind:numOfAnswers="numOfAnswers"
        @userAnswer="updateAnswers"
      />
    </div>

    <div id="summary" v-if="summaryStage">
      <h1>Summary:</h1>
      <Summary v-bind:answers="quizAnswers" v-bind:questions="questions"/>
    </div>
  </div>
</template>

<script>
import Question from "./Question.vue";
import Summary from "./Summary.vue";

export default {
  Name: "Questions",
  components: {
    Question,
    Summary
  },
  props: {
    questions: {
      type: Array,
      required: true
    }
  },
  data: function() {
    return {
      quizAnswers: [],
      numOfAnswers: 1,
      quizStage: true,
      summaryStage: false
    };
  },
  methods: {
    updateAnswers(variable) {
      //console.log("Parent: " + variable);
      this.quizAnswers.push("" + variable);
      this.numOfAnswers++;
      //console.log("QUIZ array: " + this.quizAnswers);
      //console.log(this.numOfAnswers);
      if (this.numOfAnswers === 6) {
        this.quizStage = false;
        this.summaryStage = true;
      }
    }
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Open+Sans&display=swap");
body {
  background-color: maroon;
  font-family: "Open Sans", sans-serif;
}
p {
  color: white;
}
#questions,
#summary {
  background-color: white;
  text-align: center;
  width: 100%;
}
#summary ol {
  display: inline-block;
  text-align: center;
}
</style>